---
title: "Web application in Tomcat6 with GUI"
date: 2009-09-23
forum: Desktop Environments
---

### Post by kageki on 2009-09-23
Not sure if this is the right section to post this but since I`m running my web application on Ubuntu Desktop, I`ll post it here.
 
I have a Java web application packaged into a .war file running in Tomcat6 on Windows XP. The special thing about this web application is that it displays a JFrame. On Windows XP, the JFrame displays and the web application also runs fine.
 
I recently tried running the same web application on Ubuntu Desktop but got a HeadlessException. I did some searching on the internet and found out that it has to do with the headless property. So I set Djava.awt.headless=false. I then got another exception java.langNoClassDefFoundError: Could not initialize class sun.awt.X11GraphicsEnvironment
 
Can really seem to understand why I am not allowed to display a JFrame. Can someone kindly shed some light on this matter please.

---

### Post by betolima on 2009-09-29
Hi kageki,

Could you tell how are you trying to display this JFrame ? Maybe posting the code ? 

[]s
Beto

---

