---
title: "Problem installing Tomcat 6 on server"
date: 2009-02-25
forum: General Help
---

### Post by RCholic on 2009-02-25
I got a new dedicated server delivered today and I tried to install tomcat 6 on Ubuntu 8.10. 

I first successfully installed Sun Java JDK 1.6.0.10 and JRE. 

When I try to shut down tomcat in the bin folder of tomcat by running ./shutdown.sh, I got this error:

> Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/catalina/startup/Bootstrap
Caused by: java.lang.ClassNotFoundException: org.apache.catalina.startup.Bootstrap
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: org.apache.catalina.startup.Bootstrap.  Program will exit.


Although the start.sh script seems to work, but I still cannot access tomcat by [http://66.197.161.133:8080](http://66.197.161.133:8080)  I wonder what might be wrong?

thanks

---

