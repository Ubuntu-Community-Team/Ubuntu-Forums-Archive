---
title: "Warsow ( free FPS like quake3 )"
date: 2006-06-07
forum: Gaming &amp; Leisure
---

### Post by homerhomer on 2006-06-07
I recently install Warsow and was very impressed with the quality of it.

Linux Installer 
[http://www.liflg.org/?catid=6&gameid=72](http://www.liflg.org/?catid=6&gameid=72)
or you can use the torrent attached to this post 

Cool Screenshots
[http://www.warsow.net/?p=screens](http://www.warsow.net/?p=screens)

One small trick after installing it.  In order to find on-line games you need to start the JAVA game browser. 

to install JAVA type the following a command line
sudo apt-get install sun-java5-jre


then to run the browser goto the command line and type
cd /home/USERNAME/games/warsow/browser/
/usr/bin/java -jar /home/USERNAME/games/warsow/browser/wswBrowser.jar


see ya there

---

### Post by charlieg on 2006-06-08
Something tells me you didn't search before posting...

[http://www.ubuntuforums.org/showthread.php?t=184367&highlight=warsow](http://www.ubuntuforums.org/showthread.php?t=184367&highlight=warsow)

---

### Post by chadk on 2006-06-08
If Warsow impressed you, wait till you see Enemy Territory.
[http://www.splashdamage.com/](http://www.splashdamage.com/)

---

### Post by zrothe on 2006-07-04
When I do this I get:

> aaron@knapp:~/.warsow$ /usr/bin/java -jar /home/aaron/.warsow/browser/wswBrowser.jar
Exception in thread "main" java.lang.UnsupportedClassVersionError: alx/wswbrowser/Main (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)


---

### Post by zrothe on 2006-07-04
Ok, I think it was because I had 1.4 instead of 1.5 jre

---

