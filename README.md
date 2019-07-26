# Servlet-and-jsp
How to install jsp and servlet
Servlet

They are java programs run on server. They used to handle request from server, process the request and produce the response. And send the response back to the server..

Architecture
Architecture diagram
CGI

Before servlet we were using CGI(Common Gateway Interface). Its dis advantages are.

It us platform depended language c,c++,perl

for each request, it start new process. so if there is 100 client, it start 100 process.

number of client increases, it take more time for sending response.

It cannot handle cookie

Its more expensive than servlet.
Servlet Installation.

1 install jdk https://www.oracle.com/technetwork/java/javase/downloads/index.html

2 install web server https://tomcat.apache.org/. Once downloaded extract and copy the folder in c driver.

3 set environment variable.

CATALINA =C:\apache-tomcat-9.0.22

CATALINA_HOME =C:\apache-tomcat-9.0.22;C:\apache-tomcat-9.0.22\bin\startup.bat

CLASSPATH = %CATALINA%\lib\servlet-api.jar;%CLASSPATH%

JAVA_HOME = C:\Program Files\Java\jdk-12.0.2

path =C:\Program Files\Java\jdk-12.0.2\bin
Life Cycle

    The servlet is initialized by calling the init() method.
    The servlet calls service() method to process a client’s request.
    The servlet is terminated by calling the destroy() method.
    Finally, servlet is garbage collected by the garbage collector of the JVM.

Init()

    Called only once
    Called when servlet creatyed and not called for request from user afterwards
    its one time initialization

public void init() throws ServletException {
   // Initialization code...
}

Service()

Web server call this method to handle request from client and to write response back to them.

It checks Http type(Get,Post) and calls doGet,doPost

public void service(ServletRequest request, ServletResponse response) 
   throws ServletException, IOException {
}public void doGet(HttpServletRequest request, HttpServletResponse response)
   throws ServletException, IOException {
   // Servlet code
}public void doPost(HttpServletRequest request, HttpServletResponse response)
   throws ServletException, IOException {
   // Servlet code
}

Destroy()

Calls only once at the end of life cycle

Its to close database connection, write cookie and perfor cleanup activity . and then garbage occurs

public void destroy() {
   // Finalization code...
}

Directory Structure
Directory Structure
Simple Program

index.html

<a href=”Hello”>click</a>

Hello.java

import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;public class Hello extends HttpServlet
{public void service(HttpServletRequest req, HttpServletResponse res)throws ServletException, IOException
{
PrintWriter p=res.getWriter();
p.println("Hello World");}}

web.xml

<web-app>
<servlet>
<servlet-name>sayeed</servlet-name>
<servlet-class>Hello</servlet-class>
</servlet><servlet-mapping>
<servlet-name>sayeed</servlet-name>
<url-pattern>/Hello</url-pattern>
</servlet-mapping></web-app>
