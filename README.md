
Krazytech
Login application in Java using MVC and MySQL

This Java login application follows MVC architecture and consists of Java servlets, JSPs. It uses the MySQL database server to refer to the user details. The input fields are validated using javascript.

What is a Model View Controller architecture?
The model (DAO) consists of application data and business rules, and the controller (Servlet) acts as an interface between views and model. It mediates input, converting it to commands for the model or view. A view (JSP) can be any output representation of data, such as a chart or a diagram, generally HTML or JSP page.

Here DAO is the Data Access Object – This part concentrates on business logic and database server connections and operations.

Use any IDE – Integrated development environment to minimize your work. If you haven’t started using any IDE, go get one. You will fall in love with it. I would recommend you to use Eclipse for Java applications. Link to download Eclipse. It is an open-source tool.

This application is explained thoroughly with appropriate comments and tested in Eclipse IDE. Please write comments if you find any difficulty while understanding the application.

Suggested Read:

Java Registation Page using MVC
Session and Role based Java Login example
Simple Login example in AngularJS
It is advised to segregate different components in a standard directory structure as shown below. Start your programming with  New Project -> dynamic web application project type.


Eclipse directory structure for Java MVC authentication form
Eclipse directory structure showing Packages, XML and dependent JARs



Login details are forwarded to LoginServlet from the Login.jsp page. When you click on the Login button the request is forwarded to the page which is mentioned in the action tag of the form so here the request will be forwarded to LoginServlet.java class.



Login.jsp

<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
 pageEncoding="ISO-8859-1"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
<title>Login</title>
<script> 
function validate()
{ 
  var username = document.form.username.value; 
  var password = document.form.password.value;

  if (username==null || username=="")
  { 
  alert("Username cannot be blank"); 
  return false; 
  }
  else if(password==null || password=="")
  { 
  alert("Password cannot be blank"); 
  return false; 
  } 
}
</script> 
</head>
<body>
 <div style="text-align:center"><h1>Login application in Java using MVC and MySQL </h1> </div>
 <br>
 <form name="form" action="LoginServlet" method="post" onsubmit="return validate()">
  <!-- Do not use table to format fields. As a good practice use CSS -->
  <table align="center">
   <tr>
   <td>Username</td>
   <td><input type="text" name="username" /></td>
   </tr>
   <tr>
   <td>Password</td>
   <td><input type="password" name="password" /></td>
   </tr>
   <tr> <!-- refer to the video to understand request.getAttribute() -->
   <td><span style="color:red"><%=(request.getAttribute("errMessage") == null) ? ""
   : request.getAttribute("errMessage")%></span></td>
   </tr>
   <tr>
   <td></td>
   <td><input type="submit" value="Login"></input><input
   type="reset" value="Reset"></input></td>
   </tr>
  </table>
 </form>
</body>
</html>
