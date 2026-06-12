---
title: "Tomcat Install Problem: Cannot find catalina.sh"
date: 2006-03-21
forum: Desktop Environments
---

### Post by bunter on 2006-03-21
I followed the Tomcat installation instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=44006](http://ubuntuforums.org/showthread.php?t=44006)

However, when I try to start Tomcat, I get this error:

"Cannot find /usr/local/tomcat/bin/catalina.sh"

I looked in the directory and the file is there. The path is correct too.

Can anyone tell me what I might be doing wrong?

Thanks

---

### Post by mduduzi on 2006-04-02
Check the executable permissions on the concerned files.

---

### Post by Keffin on 2006-04-02
[quote=bunter]I followed the Tomcat installation instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=44006]("http://ubuntuforums.org/showthread.php?t=44006")

However, when I try to start Tomcat, I get this error:

"Cannot find /usr/local/tomcat/bin/catalina.sh"

I looked in the directory and the file is there. The path is correct too.

Can anyone tell me what I might be doing wrong?

Thanks[/quote]

export CATALINA_HOME=/the/path/to/apache-tomcat-5.5.16

startup.sh is probably relying on this being set to find catalina.sh, as well as libraries.

---

### Post by bunter on 2006-04-04
Thanks for the replies.

I found the problem. It turns out that I installed the Sun JRE, but forgot to install the Java SDK as well. Tomcat install went smoothly after that.

---

