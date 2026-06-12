---
title: "Minecraft crashes in 10.10!"
date: 2011-03-06
forum: Gaming &amp; Leisure
---

### Post by Cam! on 2011-03-06
Minecraft was IMMENSELY slow on my Alpha of 11.03, so I switched back to 10.10 and installed the proprietary ATI drivers. The game launches really fast, but when it gets to the Mojang (Dev) logo, it crashes. What can I do to fix this?

Here are my specs, BTW.

**CPU:** Intel Q6600 (Quad Core, 2.4GHz)
**GFX:** ATI Radeon HD 6850 (1GB)
**RAM:** 4GB

---

### Post by mmsmc on 2011-03-06
do you have a crash report?

---

### Post by Cam! on 2011-03-06
No. It starts up, and just automatically exits.

---

### Post by mmsmc on 2011-03-06
start minecraft through terminal using java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame

---

### Post by Cam! on 2011-03-06
I got another error message from the terminal.

[I]Exception in thread "main" java.lang.NoClassDefFoundError: net/minecraft/LauncherFrame
Caused by: java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
	at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:248 )
Could not find the main class: net.minecraft.LauncherFrame.  Program will exit.
[/I]

---

### Post by mmsmc on 2011-03-06
open system>preferences>and then look for java 6, post if you see it

---

### Post by Cam! on 2011-03-06
I see OpenJDK 6 Policy Tool.

---

### Post by mmsmc on 2011-03-06
uninstall that in synaptic, then install java 6 enter java 6 in search, to uninstall openjdk, type it into synaptic and mark in for uninstallation

---

### Post by Cam! on 2011-03-06
I already installed Sun Java 6, and I'm currently using that. Now when logging into Minecraft, I get a black screen.

---

### Post by mmsmc on 2011-03-06
you cant have both openjdk and java installed

---

### Post by Cam! on 2011-03-06
I think this is now a graphics card problem. When opening any app that requires 3D graphics, I get a black screen. 

How do I fix this?

---

### Post by mmsmc on 2011-03-06
try opening minecraft in terminal again, that previous error was telling you that minecraft cannot open because you did not have only java installed

---

### Post by MaliciousPig on 2011-03-08
I have this exact issue, I have completely uninstalled openJDK, running from the terminal gives me the same error as listed here. I have Java 6 installed, the only Java I have.

---

### Post by jobbybobby on 2011-03-08
I have a similar problem. I am using 10.10, and after I log in on minecraft 1.3, I get a black screen, followed by this error message:

 Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to [email]support@mojang.com[/email].
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 3/8/11 5:04 PM

Minecraft: Minecraft Beta 1.3_01
OS: Linux (amd64) version 2.6.35-27-generic
Java: 1.6.0_24, Sun Microsystems Inc.
VM: Java HotSpot(TM) 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
    at org.lwjgl.opengl.Display.create(Display.java:846)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(SourceFile:260)
    at net.minecraft.client.Minecraft.run(SourceFile:632)
    at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT 524d592 ----------

---

### Post by mmsmc on 2011-03-08
do you have openjdk and java installed

---

### Post by mmsmc on 2011-03-08
any body that has this problem, go to the irc minecrfta chennel(its on minecraft.net>community) they are the experts

---

### Post by jobbybobby on 2011-03-08
> **mmsmc said:**
> do you have openjdk and java installed

nope, just java.

---

