---
title: "Java &amp; Firefox 1.0.7 + Easyubuntu 2.4 Beta4"
date: 2006-01-05
forum: General Help
---

### Post by zorglub on 2006-01-05
Hello !

I'm running Breezy. I've installed Easyubuntu 2.4 Beta 4 and I cannot access to a site with an .jsp extension url anymore.

Firefox sends me the error message reproduced hereafter. I didn't have this problem before.

doing java -version sends me this:

java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

I'm in a big trouble because I really need to access this site for my everyday's job

Any idea how to fix it ? Thanks in advance for any suggestion !


=========================================================================

Error 500--Internal Server Error

java.lang.NullPointerException
    at jsp_servlet._syndication.__getsiteparam_46_include._jspService(Ljavax.servlet.http.HttpServletRequest;Ljavax.servlet.http.HttpServletResponse;)V(getSiteParam.include.jsp:10)
    at weblogic.servlet.jsp.JspBase.service(Ljavax.servlet.ServletRequest;Ljavax.servlet.ServletResponse;)V(JspBase.java:33)
    at weblogic.servlet.internal.ServletStubImpl$ServletInvocationAction.run()Ljava.lang.Object;(ServletStubImpl.java:1006)
    at weblogic.servlet.internal.ServletStubImpl.invokeServlet(Ljavax.servlet.ServletRequest;Ljavax.servlet.ServletResponse;Lweblogic.servlet.internal.FilterChainImpl;)V(ServletStubImpl.java:419)
    at weblogic.servlet.internal.ServletStubImpl.invokeServlet(Ljavax.servlet.ServletRequest;Ljavax.servlet.ServletResponse;)V(ServletStubImpl.java:315)
    at weblogic.servlet.internal.RequestDispatcherImpl.include(Ljavax.servlet.ServletRequest;Ljavax.servlet.ServletResponse;Z)V(RequestDispatcherImpl.java:638)
    at weblogic.servlet.internal.RequestDispatcherImpl.include(Ljavax.servlet.ServletRequest;Ljavax.servlet.ServletResponse;)V(RequestDispatcherImpl.java:423)
    at weblogic.servlet.jsp.PageContextImpl.include(Ljava.lang.String;)V(PageContextImpl.java:154)
    at jsp_servlet._syndication._1lc4zuukokam.__homepage._jspService(Ljavax.servlet.http.HttpServletRequest;Ljavax.servlet.http.HttpServletResponse;)V(homepage.jsp:17)
    at weblogic.servlet.jsp.JspBase.service(Ljavax.servlet.ServletRequest;Ljavax.servlet.ServletResponse;)V(JspBase.java:33)
    at weblogic.servlet.internal.ServletStubImpl$ServletInvocationAction.run()Ljava.lang.Object;(ServletStubImpl.java:1006)
    at weblogic.servlet.internal.ServletStubImpl.invokeServlet(Ljavax.servlet.ServletRequest;Ljavax.servlet.ServletResponse;Lweblogic.servlet.internal.FilterChainImpl;)V(ServletStubImpl.java:419)
    at weblogic.servlet.internal.ServletStubImpl.invokeServlet(Ljavax.servlet.ServletRequest;Ljavax.servlet.ServletResponse;)V(ServletStubImpl.java:315)
    at weblogic.servlet.internal.WebAppServletContext$ServletInvocationAction.run()Ljava.lang.Object;(WebAppServletContext.java:6718)
    at weblogic.security.acl.internal.AuthenticatedSubject.doAs(Lweblogic.security.subject.AbstractSubject;Ljava.security.PrivilegedAction;)Ljava.lang.Object;(AuthenticatedSubject.java:321)
    at weblogic.security.service.SecurityManager.runAs(Lweblogic.security.acl.internal.AuthenticatedSubject;Lweblogic.security.acl.internal.AuthenticatedSubject;Ljava.security.PrivilegedAction;)Ljava.lang.Object;(SecurityManager.java:121)
    at weblogic.servlet.internal.WebAppServletContext.invokeServlet(Lweblogic.servlet.internal.ServletRequestImpl;Lweblogic.servlet.internal.ServletResponseImpl;)V(WebAppServletContext.java:3764)
    at weblogic.servlet.internal.ServletRequestImpl.execute(Lweblogic.kernel.ExecuteThread;)V(ServletRequestImpl.java:2644)
    at weblogic.kernel.ExecuteThread.execute(Lweblogic.kernel.ExecuteRequest;)V(ExecuteThread.java:219)
    at weblogic.kernel.ExecuteThread.run()V(ExecuteThread.java:178)
    at java.lang.Thread.startThreadFromVM(Ljava.lang.Thread;)V(Unknown Source)

---

### Post by Arcturus691 on 2008-04-28
I also tried to use a web site that uses a .jsp extension and firefox does not know what to do with it.  In this case it is a button that executes a search on an ATT web page.  When clicking on the "Go" button fire fox opens a dialog "Opening File index.jsp" and asks me if I want to save it or browse for an app that will open the file.  Not sure if this is the same issue because my setup is different then yours.

xxxxx@xxxxx:~$java -version
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b22)
IcedTea 64-Bit Server VM (build 1.7.0-b22, mixed mode)

Firefox Help->About:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.8.1.14) Gecko/20080418 Ubuntu/7.10 (gutsy) Firefox/2.0.0.14

---

