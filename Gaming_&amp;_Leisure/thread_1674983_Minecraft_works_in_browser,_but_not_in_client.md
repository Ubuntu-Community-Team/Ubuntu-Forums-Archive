---
title: "Minecraft works in browser, but not in client"
date: 2011-01-24
forum: Gaming &amp; Leisure
---

### Post by rhythmatic on 2011-01-24
Hey, I recently reinstalled Ubuntu 10.10 on my machine. I had minecraft running flawlessly beforehand, but now I can't get it working. I just spent the last 4 hours googling and searching the forums for anything that seemed related, and after trying a few different things such as adding libraries or switching to other versions of java, I am stumped. Here are the outputs I get from a few commands, just to get you started off.

[COLOR=#bf0000]EDIT:[/COLOR] The game works perfectly in browser.


```
kingpin@BONSAITREE:~/.minecraft$ java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
Exception in thread "main" java.lang.NoClassDefFoundError: net/minecraft/LauncherFrame
Caused by: java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: net.minecraft.LauncherFrame. Program will exit.
``````
kingpin@BONSAITREE:~/.minecraft$ java -jar minecraft.jar
Failed to load Main-Class manifest attribute from
minecraft.jar
```

---

### Post by proteusmoteus on 2011-01-24
First of all is the Minecraft.jar from minecraft.net in ~/.minecraft? There is a different minecraft.jar located in ~/.minecraft/bin that is completely different (not launch-able to my knowledge). Since you are having problems I would recommend reaquiring the file via logging in to Minecraft.net and clicking the "Download" link on the right side of the page.

---

### Post by rhythmatic on 2011-01-26
Oh my god, that worked. Thanks. ^_^;;

---

