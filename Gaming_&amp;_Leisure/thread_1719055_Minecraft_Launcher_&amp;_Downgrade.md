---
title: "Minecraft Launcher &amp; Downgrade"
date: 2011-04-01
forum: Gaming &amp; Leisure
---

### Post by TRUCKERm on 2011-04-01
Could anyone offer me a minecraft launcher for ubuntu 10.4 aswell as a downgrader?

A friend of mine once did a launcher.sh launcher for me but I had to reinstall ubuntu due to a bug and now I do not have that anymore. 
So..I need a working launcher and downgrade (downgrade to 1.2 instructions or downgrader) help.

I hope that someone can help me.

This is the error I get when starting minecraft over sudo java minecraft.jar 
Exception in thread "main" java.lang.NoClassDefFoundError: minecraft/jar
Caused by: java.lang.ClassNotFoundException: minecraft.jar
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: minecraft.jar. Program will exit.

---

### Post by Quadunit404 on 2011-04-01
Run this:

```
java -jar Minecraft.jar
```

in the folder Minecraft is located in. sudo isn't necessary for Minecraft.

---

### Post by PunkLV on 2011-04-03
Posting in Minecraft thread.

I've been running a server on a headless machine over ssh for my friends, however I couldn't manage to run in without invoking **nohup**. It'd be awesome to safely logout of ssh and server with it's open prompt would keep on running. Sending it to background crashes it. Tried screen, tmux same thing.

Any advice or suggestions?

---

