---
title: "Java 500 Error"
date: 2006-08-24
forum: Desktop Environments
---

### Post by rlreich on 2006-08-24
I've got an ISP that requires a web based login. I can login fine with IE but not with Firefox. I get the following error:

500 Servlet Exception

java.lang.NumberFormatException: null
	at java.lang.Integer.parseInt(Integer.java:414)
	at java.lang.Integer.<init>(Integer.java:549)
	at scpservlet.UserDataReqLoginServlet.service(UserDataReqLoginServlet.java:51)
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:103)
	at com.caucho.server.http.FilterChainServlet.doFilter(FilterChainServlet.java:82)
	at com.caucho.server.http.Invocation.service(Invocation.java:278)
	at com.caucho.server.http.CacheInvocation.service(CacheInvocation.java:129)
	at com.caucho.server.http.RunnerRequest.handleRequest(RunnerRequest.java:338)
	at com.caucho.server.http.RunnerRequest.handleConnection(RunnerRequest.java:270)
	at com.caucho.server.TcpConnection.run(TcpConnection.java:140)
	at java.lang.Thread.run(Thread.java:484)

Resin 2.0.4 (built Thu Nov 15 17:56:24 PST 2001)

I need to get online so I can install Wine. I've tried doing it offline but being a newbie I guess I'm messing something up in the process. Does anyone know what this error means? Or is there an IE clone that I can install on the Ubu side that will let me get around this? I've tried Opera on the Win side also and it will not work either. BTW this is a Chinese ISP. Thanks for the help!

---

