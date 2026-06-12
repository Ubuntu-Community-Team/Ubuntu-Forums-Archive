---
title: "How to i can running .jsp page on Firefox or Chromium"
date: 2015-06-05
forum: Desktop Environments
---

### Post by Basshunter on 2015-06-05
My company have 100 Desktop computers (Dell Inspriron 3647) running Ubuntu OS.
But we have problem about ERP system. i can not running .jsp webpage on Firefox or Chromium, i installed java 6, 7, 8.
actually ERP website compatible with Internet Explorer 8 & Java 6u16
I try PlayonLinux but it is same crash. 
How to i can running it ? i am sorry, i am not good english.
---------------------------------.
thank you very much

---

### Post by mörgæs on 2015-06-05
Hi, welcome to the fora.

JSP is short for Java Server Page, which indicates that Java is active on serverside, not on the client.

I don't think installing a Java environment on clientside is going to make a difference. Please tell exactly what the problem is.

---

### Post by Basshunter on 2015-06-05
Thanks for your reply.
My ERP Server running Redhat, Oracle database. client computer login ERP by address: [http://ip-erp-server/login.jsp](http://ip-erp-server/login.jsp)
but all web browser can not enable Java Runtime Environment. I check my PC: java -version is ok.
So i think i should try more solutions, and i can show detail my bug. Thanks you more

---

### Post by mörgæs on 2015-06-07
The link does not work. It's probably taken from your intranet.

Again, what exactly is the problem? Please show a log file, an error message or something similar. 

If you want to verify that a Java runtime environment is working in the browser, the page [www.javatester.org/]("http://www.javatester.org/") is worth seeing. As mentioned above it should not be necessary for JSP, but of course it's handy for other sites.

---

