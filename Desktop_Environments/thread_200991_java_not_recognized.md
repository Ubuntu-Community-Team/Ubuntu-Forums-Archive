---
title: "java not recognized"
date: 2006-06-21
forum: Desktop Environments
---

### Post by e-blade on 2006-06-21
After upgrading from GNU's java compiler to SUN's java compiler using synaptic (JRE/JDK, docs etc) was installed.
Afterwards however i deleted the 1.4.2-gjc-java-something from /usr/lib/jvm/, did update-alternatives --config java and thought that was it.

Unfortunately when i use 'java -version' from the console bash wont recognize it anymore. What the deal with this?

---

### Post by Skerit on 2006-06-21
Have thesame issue,

when I install the official java from the repo it messes up the symlinks (or whatever it works with)

'javac' works fine but 'java' just does nothing... I guess there is a fix but I kinda want it to work the way it's supposed to work.. Gonna try to completely remove every trace of java and then reinstall it...

---

### Post by e-blade on 2006-06-21
let me know if it works out :D

---

