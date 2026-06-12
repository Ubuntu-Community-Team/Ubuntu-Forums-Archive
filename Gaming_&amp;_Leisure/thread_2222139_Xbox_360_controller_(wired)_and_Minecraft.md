---
title: "Xbox 360 controller (wired) and Minecraft"
date: 2014-05-05
forum: Gaming &amp; Leisure
---

### Post by thebrandon on 2014-05-05
I have dug around and tried every tutorial I can and I cant seem to get this to work.  Ubuntu recognizes the controller, I get output in jtest.   I can map the buttons in zsnes.   But when I try to get the buttons to map in Minecraft I get nothing.  I feel like I am missing something that maybe tells java to recognize the controller?

I also tried Minecontrol but when I run it I get this output :

brandon@brandon-desktop:~/minecraft$ java -jar Minecontrol.jar
Exception in thread "main" java.lang.NoClassDefFoundError: org/ini4j/Ini
	at com.joshjcarrier.minecontrol.services.storage.IniStorage.<init>(IniStorage.java:18)
	at com.joshjcarrier.minecontrol.services.ProfileStorageService.<init>(ProfileStorageService.java:29)
	at com.joshjcarrier.minecontrol.services.RunnableGamePadInterpreter.<init>(RunnableGamePadInterpreter.java:25)
	at com.joshjcarrier.minecontrol.App.<init>(App.java:21)
	at com.joshjcarrier.minecontrol.App.main(App.java:48)
Caused by: java.lang.ClassNotFoundException: org.ini4j.Ini
	at java.net.URLClassLoader$1.run(URLClassLoader.java:366)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:355)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:354)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:425)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:308)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:358)
	... 5 more

---

### Post by Ranko Kohime on 2014-05-05
> **thebrandon said:**
> I have dug around and tried every tutorial I can and I cant seem to get this to work.  Ubuntu recognizes the controller, I get output in jtest.   I can map the buttons in zsnes.   But when I try to get the buttons to map in Minecraft I get nothing.  I feel like I am missing something that maybe tells java to recognize the controller?
Some games have issues with controllers even when jstest gives output, due to security issues in Ubuntu (the security is a little overtight, is the issue)

Check out [this post on the Steam forums]("http://steamcommunity.com/app/221410/discussions/0/864959809809029907/#c864973032768211300") and see if it works for you.

---

