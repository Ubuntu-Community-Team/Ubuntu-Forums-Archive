---
title: "Xubuntu Minecraft Crash"
date: 2011-09-28
forum: Gaming &amp; Leisure
---

### Post by cynt_ on 2011-09-28
Hi guys. I recently formatted my pc from windows xp performance to Xubuntu 11.04 but now it seems like I can't play minecraft.
When I launch it, i log in, and then the following error report pops out:


```

      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to [EMAIL="support@mojang.com"]support@mojang.com[/EMAIL].
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 9/28/11 10:17 PM

Minecraft: Minecraft Beta 1.8.1
OS: Linux (i386) version 2.6.38-11-generic
Java: 1.6.0_26, Sun Microsystems Inc.
VM: Java HotSpot(TM) Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: Could not init GLX
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
    at org.lwjgl.opengl.Display.create(Display.java:854)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(Minecraft.java:266)
    at net.minecraft.client.Minecraft.run(Minecraft.java:598)
    at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT 3ccb9ebb ----------

```If anyone could be of any assistance it would be greatly appreciated.
Graphics adapter:  SIS Mirage 3 671MX

---

### Post by cynt_ on 2011-09-29
Ok, so I did some research and I found this guy with the exact same problem except with nvidia drivers. Could someone adapt his solution to my graphics card? Thank you

---

### Post by cynt_ on 2011-09-29
I forgot to post the link lol [http://ubuntuforums.org/showthread.php?t=1810956](http://ubuntuforums.org/showthread.php?t=1810956)

---

