---
title: "Eclipse Class Not Found"
date: 2009-04-29
forum: General Help
---

### Post by ekaqu on 2009-04-29
I just upgraded to 9.4 the other day and went to start working on my program for class.  I normally work with vi/terminal while coding but I was having an issue that needed the use of a debugger, so I opened up eclipse, started a new project for the code and went to run the tester.

> Exception in thread "main" java.lang.NoClassDefFoundError: ID3Tester
Caused by: java.lang.ClassNotFoundException: ID3Tester
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: ID3Tester.  Program will exit.

It seems that when I make any new projects, eclipse is unable to find the .class files.

So I did a little digging and found this [http://coding.derkeiler.com/Archive/Java/comp.lang.java.softwaretools/2004-10/0044.html]("http://coding.derkeiler.com/Archive/Java/comp.lang.java.softwaretools/2004-10/0044.html")

I tried checking to see what java eclipse was using and its java-6-sun-1.6.0.13 which is my default JDK.

Thank you for your time in reading this.

---

