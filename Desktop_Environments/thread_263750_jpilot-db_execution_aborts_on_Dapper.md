---
title: "jpilot-db execution aborts on Dapper"
date: 2006-09-23
forum: Desktop Environments
---

### Post by einstein on 2006-09-23
Greetings Folks!

I am having a problem executing the jpilot-db jar file on Dapper.  When attempting to execute, the jpilot-db splash screen appears for about a half second then I get error messages.  The same file works (executes) fine on Win XP :( so I do not think the problem is in the jar file.

I have copied my command line and the resulting messages from the terminal below.  Can anyone tell me what I doing wrong?  I have done a lot of Googling but came empty.  By the way, there is a 'pilotdb.ui.Application' path in the jar file but not a 'javax.help.HelpSet' (although the 'javax' directory does exist).

dennis@ubuntu-d1:~/Desktop$ java -jar jpilot-db-1.3.20-ej.jar
Exception in thread "main" java.lang.NoClassDefFoundError: pilotdb.ui.Application
   at java.lang.Class.initializeClass(libgcj.so.7)
   at pilotdb.ui.GUI.start(GUI.java:14)
   at pilotdb.tools.Tools.main(Tools.java:92)
Caused by: java.lang.ClassNotFoundException: javax.help.HelpSet not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:jpilot-db-1.3.20-ej.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.ClassLoader.loadClass(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   ...2 more
dennis@ubuntu-d1:~/Desktop$

Thanks in advance.

---

### Post by einstein on 2006-09-23
Ahhhh,,, okay....  Could someone at least tell me whether the command line looks correct?

---

### Post by einstein on 2006-09-24
I have resolved the problem - wrong java installed.  Works now.  Thanks.

---

### Post by jazzbox on 2006-11-08
I've just run into the same problem.  Which java package did you need to install?

---

### Post by einstein on 2006-11-11
Hi jazzbox;

Sorry, I cannot remember which Java was required nor can I find the installation file.  However, in a terminal I did:

dennis@ubuntu-d1:/$ cd /usr/share/java
dennis@ubuntu-d1:/usr/share/java$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

Hope this helps a bit.  I do seem to recall I that downloaded a .tar.gz file from Sun Microsystems though.

Regards, Dennis

---

