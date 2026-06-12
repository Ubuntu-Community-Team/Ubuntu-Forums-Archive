---
title: "More Minecraft Problems"
date: 2012-08-16
forum: Gaming &amp; Leisure
---

### Post by SirWhy on 2012-08-16
Hey guys

I made the switch from Windows 7 a little while ago and have had a great experience with Ubuntu, until now

While trying to install Minecraft on Natty but have had problems. 

First time round, I install and I get a login screen, that's great. Make a new game then CRASH. Search some forums and re-install video drivers.

Second time, I get a login screen, login then CRASH, this time though with a nice error message which I have lovingly put in some code tags for you

```


      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem; Failed to start game
This error has been saved to /home/mark/.minecraft/crash-reports/crash-2012-08-16_21.42.42-client.txt for your convenience. Please include a copy of this file if you report this crash to anyone.



--- BEGIN ERROR REPORT faffba06 --------
Generated 16/08/12 21:42

- Minecraft Version: 1.3.2
- Operating System: Linux (i386) version 2.6.38-15-generic
- Java Version: 1.6.0_33, Sun Microsystems Inc.
- Java VM Version: Java HotSpot(TM) Server VM (mixed mode), Sun Microsystems Inc.
- Memory: 42446776 bytes (40 MB) / 84148224 bytes (80 MB) up to 704643072 bytes (672 MB)
- JVM Flags: 0 total; 
- LWJGL: 2.4.2
- OpenGL: Gallium 0.4 on AMD RV710 GL version 1.4 (2.1 Mesa 7.10.2), X.Org
- Is Modded: Probably not
- Type: Client
- Texture Pack: Default
- Profiler Position: N/A (disabled)

org.lwjgl.LWJGLException: X Error - disp: 0x9009568 serial: 101 error: GLXBadRenderRequest request_code: 155 minor_code: 1
	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:268)
	at org.lwjgl.opengl.GL11.nglGenTextures(Native Method)
	at org.lwjgl.opengl.GL11.glGenTextures(GL11.java:1376)
	at anh.a(SourceFile:20)
	at avf.a(SourceFile:167)
	at aov.<init>(SourceFile:88)
	at net.minecraft.client.Minecraft.a(SourceFile:246)
	at net.minecraft.client.Minecraft.run(SourceFile:516)
	at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT 650ce1a0 ----------
```

So now I turn to the community, thanks guys.

---

### Post by efflandt on 2012-08-16
What video do you have (appears to be AMD/ATI) and what video drivers are you using (default radeon, or fglrx)?

I have run minecraft since 1.8 beta in 64-bit Ubuntu 10.10, 11.10, and currently 12.04 using openjdk-6.  I am using lwjgl 2.6, but only due to an occasional stuck movement key issue with the lwjgl 2.4.2 that comes with minecraft.

Although, the only computer I have with modern Radeon HD video is a 2 GB tablet PC with AMD C-50 cpu at a leisurely 1 GHz 2 core, which is playable booting 64-bit Ubuntu from SD card (20-30 fps @ 1280x800). 

Typical way to launch minecraft is to cd to the directory containing the original minecraft.jar launcher (not the one in ~/.minecraft/bin/) and do:

```
java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
```or do that (with either the cd or full path to minecraft.jar) from a script in your ~/bin

---

### Post by SirWhy on 2012-08-16
I downloaded the drivers from ATI but by the looks of it they are fglrx anyway

---

