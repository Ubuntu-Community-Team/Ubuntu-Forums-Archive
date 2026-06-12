---
title: "Frostwire Problem!"
date: 2006-06-07
forum: Desktop Environments
---

### Post by DimitrisC on 2006-06-07
Hello, I installed t frostwire, when I execute frostwire at terminal I get:

Quote:
[dimitris@linuxbox]# frostwire
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in /usr/lib/ hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in /usr/java/ hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in /opt/ hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
When I check my java version at [www.java.com](www.java.com) it tells me that I'm running 1.5.0_06 but when I use java -version I get 1.4.2. What do i have to do to get frostwire to work?
Thank you

---

### Post by chiefofthejojos on 2006-06-12
```
/usr/lib/jvm/java-1.5.0-sun/bin/java -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. -jar FrostWire.jar
``` Worked for me, but I'm sure there's a better way.

EDIT:  There is a better way.  Just remove gij.  For me that was just "sudo apt-get remove gij-4.1", if that doesn't work remove the "-4.1".

---

### Post by sheilnaik on 2006-06-12
[QUOTE=chiefofthejojos]EDIT:  There is a better way.  Just remove gij.  For me that was just "sudo apt-get remove gij-4.1", if that doesn't work remove the "-4.1".[/QUOTE]

Thanks a lot.  This helped me out too :D

---

### Post by copey02 on 2006-06-12
thanks! i just searched cause i was having the exact same problem! its all good now! thanks!

---

### Post by cosine7 on 2006-06-18
Thanks same problem here, sudo apt-get remove gij-4.1 fixed it for me too.... kudos to u chief

---

