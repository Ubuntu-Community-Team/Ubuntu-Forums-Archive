---
title: "Can't get minecraft to work."
date: 2011-09-16
forum: Gaming &amp; Leisure
---

### Post by TacticalApe on 2011-09-16
I've had this problem everytime I try to run minecraft. I installed it using the minecraftinstaller.sh, I can log in and everything, but then after I do I get this:

```
Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to support@mojang.com.
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 9/15/11 11:20 PM

Minecraft: Minecraft Beta 1.8.1
OS: Linux (i386) version 2.6.38-11-generic-pae
Java: 1.6.0_26, Sun Microsystems Inc.
VM: Java HotSpot(TM) Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
    at org.lwjgl.opengl.Display.create(Display.java:846)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(SourceFile:233)
    at net.minecraft.client.Minecraft.run(SourceFile:629)
    at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT 91a9c4fa ----------



```

Every time. It's very annoying. What do I do?

---

### Post by uRock on 2011-09-16
Bump for move to *Gaming & Leisure*.

---

### Post by mmsmc on 2011-09-16
do you have java installed(latest version?) can you play the browser version?

---

### Post by sublimnalxx on 2011-09-16
You need to install the proprietary drivers for your video card. I think you need to go to Applications, or Administration. Something like that and it will recommend a video card driver for you.

---

### Post by uRock on 2011-09-16
Typing Addi in the search field will bring up the additional drivers application.

---

### Post by TacticalApe on 2011-09-16
I got it working by updating drivers. Thanks!

---

### Post by donkyhotay on 2011-09-17
> **TacticalApe said:**
> I got it working by updating drivers. Thanks!

Don't forget to mark the thread as solved then.

---

