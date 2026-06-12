---
title: "How do I install JDK + NetBeans?"
date: 2006-09-29
forum: Desktop Environments
---

### Post by Zach1188 on 2006-09-29
I am trying to install JDK + NetBeans from here:

[https://sdlc2a.sun.com/ECom/EComActionServlet/DownloadPage:~:com.sun.sunit.sdlc.content.DownloadPageInfo;jsessionid=17B0030D37F3474E6DA906944947378A;jsessionid=17B0030D37F3474E6DA906944947378A](https://sdlc2a.sun.com/ECom/EComActionServlet/DownloadPage:~:com.sun.sunit.sdlc.content.DownloadPageInfo;jsessionid=17B0030D37F3474E6DA906944947378A;jsessionid=17B0030D37F3474E6DA906944947378A)


I downloaded the first one, and it came in a .bin file.

I tried running "sudo sh jdk-1_5_0_07-nb-5_0-linux-ml.bin" and "sh jdk-1_5_0_07-nb-5_0-linux-ml.bin", but both of them give me this:

> 
          The launcher "jdk-1_5_0_07-nb-5_0-linux-ml.bin"
          is not executable for the current user.  Please give
          execute permission for the current user before
          attempting to launch the installer.


So, how do I install it?

(Yes, I already installed JRE).

---

### Post by Zach1188 on 2006-09-29
Sorry to bump, but I really need an answer.

---

### Post by JNowka on 2006-09-30
try:
"sudo ./jdk-1_5_0_07-nb-5_0-linux-ml.bin"

Just ignore the entire sh deal.

---

### Post by T_W on 2006-09-30
Issuing the command:

chmod +x jdk-1_5_0_07-nb-5_0-linux-ml.bin 

Should allow it to be executed.

---

### Post by Zach1188 on 2006-09-30
> **JNowka said:**
> try:
"sudo ./jdk-1_5_0_07-nb-5_0-linux-ml.bin"

Just ignore the entire sh deal.
Thanks, it worked. I don't know why I didn't try it without sh...?

---

### Post by jbmech006 on 2006-10-23
simply typing sudo doest always work either, another way to install Java + NetBeans is to type: chmod 755 jdk-1_5_0_09-nb-5_0-linux-ml.bin to change the installer file's permissions so it can be executed.

---

