# java-servlet-calculator
# this is a code for simple calculator using java servlet in NetBeans.
# HTML code
<html>
    <head>
        <title>TODO supply a title</title>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
    </head>
    <body>
        <h1>My Calculator</h1><hr>
        <form action="Helo" method="post" style="background-color:gainsboro">
            Enter first number:
            <input type="number" name="n1" placeholder="first number"><br/><br/>
            Enter second number:
            <input type="number" name="n2" placeholder="second number"><br/><br/>
            Select operation: 
            <input type="radio" name="op" value="add"/>+
            <input type="radio" name="op" value="sub"/>-
            <input type="radio" name="op" value="mul"/>*
            <input type="radio" name="op" value="div"/>/
               <br/><br/>
             <input type="reset" value="reset">
             <input type="submit" value="Calculate"/>
        </form>           
    </body>
</html>

  # servlet code
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */

import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 *
 * @author vidit patsariya
 */
@WebServlet(urlPatterns = {"/Helo"})
public class Helo extends HttpServlet {

    /**
     * Processes requests for both HTTP <code>GET</code> and <code>POST</code>
     * methods.
     *
     * @param request servlet request
     * @param response servlet response
     * @throws ServletException if a servlet-specific error occurs
     * @throws IOException if an I/O error occurs
     */
    protected void processRequest(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html;charset=UTF-8");
        try (PrintWriter out = response.getWriter()) {
            /* TODO output your page here. You may use following sample code. */
            out.println("<!DOCTYPE html>");
            out.println("<html>");
            out.println("<head>");
            out.println("<title>Servlet Helo</title>");            
            out.println("</head>");
            
            int n1=Integer.parseInt(request.getParameter("n1"));
            int n2=Integer.parseInt(request.getParameter("n2"));
            String op= request.getParameter("op");
            int res=0;
            if(op.equals("add"))
            {
            res=n1+n2;
            }
            else if(op.equals("sub"))
            {
             res=n1-n2;
            }
            else if(op.equals("mul"))
            {
                res=n1*n2;
            }
            else if(op.equals("div"))
            {
                res=n1/n2;
            }
            out.println("<h1>Result="+res+"</h1>");
            out.println("Thanks for using my Calculator");
           
            out.println("</body>");
            out.println("</html>");
         }
        }
