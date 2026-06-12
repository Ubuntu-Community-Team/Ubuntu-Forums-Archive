---
title: "APFG(Awesome Pony Fighting Game)Building Issues"
date: 2013-06-04
forum: Gaming &amp; Leisure
---

### Post by TheManno1 on 2013-06-04
Using Ubuntu Studio 12.04 64bit edition.
I have some problems building the getlibs.sh can anyone help see here [https://github.com/jubilee145/APFG/issues/16](https://github.com/jubilee145/APFG/issues/16)
Can anybody help?

---

### Post by TheManno1 on 2013-06-06
Bump.

---

### Post by TheManno1 on 2013-06-07
Bump

---

### Post by TheManno1 on 2013-06-09
Bump

---

### Post by TheManno1 on 2013-06-11
Bump

---

### Post by TheManno1 on 2013-06-14
Bump

---

### Post by TheManno1 on 2013-06-16
Bump

---

### Post by TheManno1 on 2013-06-26
john@john-Aspire-5742:~/Downloads/APFG-master$ ant
Buildfile: /home/john/Downloads/APFG-master/build.xml

  compile:
     [echo] Compile and run: /home/john/Downloads/APFG-master/build.xml
  run:
     [java] Tue Jun 25 18:25:02 MSK 2013 INFO:Slick Build #261
     [java] Tue Jun 25 18:25:02 MSK 2013 INFO:LWJGL Version: 2.8.5
     [java] Tue Jun 25 18:25:02 MSK 2013 INFO:OriginalDisplayMode: 1366 x 768 x 24 @60Hz
     [java] Tue Jun 25 18:25:02 MSK 2013 INFO:TargetDisplayMode: 1280 x 764 x 0 @0Hz
     [java] Tue Jun 25 18:25:02 MSK 2013 ERROR:Could not init GLX
     [java] org.lwjgl.LWJGLException: Could not init GLX
     [java]     at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
     [java]     at org.lwjgl.opengl.LinuxDisplayPeerInfo.(LinuxDisplayPeerInfo.java:61)
     [java]     at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:788)
     [java]     at org.lwjgl.opengl.DrawableGL.setPixelFormat(DrawableGL.java:61)
     [java]     at org.lwjgl.opengl.Display.create(Display.java:843)
     [java]     at org.lwjgl.opengl.Display.create(Display.java:754)
     [java]     at org.newdawn.slick.AppGameContainer.tryCreateDisplay(AppGameContainer.java:342)
     [java]     at org.newdawn.slick.AppGameContainer.access$000(AppGameContainer.java:32)
     [java]     at org.newdawn.slick.AppGameContainer$2.run(AppGameContainer.java:407)
     [java]     at java.security.AccessController.doPrivileged(Native Method)
     [java]     at org.newdawn.slick.AppGameContainer.setup(AppGameContainer.java:388)
     [java]     at org.newdawn.slick.AppGameContainer.start(AppGameContainer.java:357)
     [java]     at svb.Main.main(Unknown Source)
     [java] Xlib:  extension "GLX" missing on display ":0.0".
     [java] Xlib:  extension "GLX" missing on display ":0.0".
     [java] Xlib:  extension "GLX" missing on display ":0.0".
     [java] org.newdawn.slick.SlickException: Failed to initialise the LWJGL display
     [java]     at org.newdawn.slick.AppGameContainer.setup(AppGameContainer.java:418)
     [java]     at org.newdawn.slick.AppGameContainer.start(AppGameContainer.java:357)
     [java]     at svb.Main.main(Unknown Source)

  BUILD SUCCESSFUL
Total time: 2 seconds
  Not running how do I run it?

---

### Post by TheManno1 on 2013-07-01
Bump.

---

