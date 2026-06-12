---
title: "Tomcat6+Ubuntu 8.10 + opengork does not work."
date: 2009-05-30
forum: General Help
---

### Post by defmer on 2009-05-30
I am trying to setup OpenGrok with tomcat6 on Ubuntu 8.10. But it won't install the app or start either. so here is where what I have done till now. I really need some freaking help with this....
status:

1) I am using the Ubuntu 8.10, tomcat 6 and opengrok 0.7
2) if I copy the source.war to /usr/share/tomcat6/webapps/- the app is nto recognized. I don't see it in the [http://127.0.0.1:8080/manager/html](http://127.0.0.1:8080/manager/html) but I see the manager and host-manager apps being listed.

3) So I copied it to /var/lib/tomcat6/webapps, I restart tomcat and I see the app, but when I start it I see " FAIL - Application at context path /source could not be started" in the tomcat manager.

4) so I looked at the logs /var/log/tomcat6/localhost.2009-05-30.log and I see 


[I]INFO: HTMLManager: start: Starting web application at '/source'
May 30, 2009 2:04:33 PM org.apache.catalina.core.StandardContext listenerStart
SEVERE: Exception sending context initialized event to listener instance of class org.opensolaris.opengrok.web.WebappListener
java.security.AccessControlException: access denied (java.io.FilePermission /opengrok/data/configuration.xml read)
at java.security.AccessControlContext.checkPermission(AccessControlContext.java:32 3)
at java.security.AccessController.checkPermission(AccessController.java:546)
at java.lang.SecurityManager.checkPermission(SecurityManager.java:532)
at java.lang.SecurityManager.checkRead(SecurityManager.java:871)
at java.io.FileInputStream.(FileInputStream.java:100)
at org.opensolaris.opengrok.configuration.Configuration.read(Configuration.java:32 9)
at org.opensolaris.opengrok.configuration.RuntimeEnvironment.readConfiguration(Run timeEnvironment.java:545)
at org.opensolaris.opengrok.web.WebappListener.contextInitialized(WebappListener.j ava:90)
at org.apache.catalina.core.StandardContext.listenerStart(StandardContext.java:384 3)
at org.apache.catalina.core.StandardContext.start(StandardContext.java:4342)
at org.apache.catalina.manager.ManagerServlet.start(ManagerServlet.java:1247)
at org.apache.catalina.manager.HTMLManagerServlet.start(HTMLManagerServlet.java:60 4)
at org.apache.catalina.manager.HTMLManagerServlet.doGet(HTMLManagerServlet.java:12 9)
at javax.servlet.http.HttpServlet.service(HttpServlet.java:617)
at javax.servlet.http.HttpServlet.service(HttpServlet.java:717)
at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39) at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.ja va:25)
at java.lang.reflect.Method.invoke(Method.java:597)
at org.apache.catalina.security.SecurityUtil$1.run(SecurityUtil.java:244)
at java.security.AccessController.doPrivileged(Native Method)
at javax.security.auth.Subject.doAsPrivileged(Subject.java:517)
at org.apache.catalina.security.SecurityUtil.execute(SecurityUtil.java:276)
at org.apache.catalina.security.SecurityUtil.doAsPrivilege(SecurityUtil.java:162)< br /> at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(ApplicationFil terChain.java:283)
at org.apache.catalina.core.ApplicationFilterChain.access$000(ApplicationFilterCha in.java:56)
at org.apache.catalina.core.ApplicationFilterChain$1.run(ApplicationFilterChain.ja va:189)
at java.security.AccessController.doPrivileged(Native Method)
at org.apache.catalina.core.ApplicationFilterChain.doFilter(ApplicationFilterChain .java:185)
at org.apache.catalina.core.StandardWrapperValve.invoke(StandardWrapperValve.java: 233)
at org.apache.catalina.core.StandardContextValve.invoke(StandardContextValve.java: 191)
at org.apache.catalina.authenticator.AuthenticatorBase.invoke(AuthenticatorBase.ja va:525)
at org.apache.catalina.core.StandardHostValve.invoke(StandardHostValve.java:128) at org.apache.catalina.valves.ErrorReportValve.invoke(ErrorReportValve.java:102) at org.apache.catalina.core.StandardEngineValve.invoke(StandardEngineValve.java:10 9)
at org.apache.catalina.connector.CoyoteAdapter.service(CoyoteAdapter.java:286)
at org.apache.coyote.http11.Http11Processor.process(Http11Processor.java:845)
at org.apache.coyote.http11.Http11Protocol$Http11ConnectionHandler.process(Http11P rotocol.java:583)
at org.apache.tomcat.util.net.JIoEndpoint$Worker.run(JIoEndpoint.java:447)
at java.lang.Thread.run(Thread.java:619)
May 30, 2009 2:04:33 PM org.apache.catalina.core.ApplicationContext log
INFO: HTMLManager: list: Listing contexts for virtual host 'localhost'
[/I]

But I already set all kinds of permissions possible on /opengrok and sub folders.
so PLEASE HELP ME OUT HERE, I am running out of ideas and please I really appreciate if you could be verbose/detailed in your answers/responce

thank you,
defmer

---

