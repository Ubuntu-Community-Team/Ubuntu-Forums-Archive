---
title: "Minecraft Run Error"
date: 2013-07-17
forum: Gaming &amp; Leisure
---

### Post by LordFran on 2013-07-17
I tried to run minecraft on ubuntu and I get this message

---- Minecraft Crash Report ----
// Don't be sad. I'll do better next time, I promise!

Time: 7/17/13 8:25 AM
Description: Initializing game

org.lwjgl.LWJGLException: Could not init GLX
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:61)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:788)
    at org.lwjgl.opengl.DrawableGL.setPixelFormat(DrawableGL.java:61)
    at org.lwjgl.opengl.Display.create(Display.java:846)
    at org.lwjgl.opengl.Display.create(Display.java:757)
    at org.lwjgl.opengl.Display.create(Display.java:739)
    at ats.O(SourceFile:297)
    at ats.d(SourceFile:599)
    at net.minecraft.client.main.Main.main(SourceFile:101)


A detailed walkthrough of the error, its code path and all known details is as follows:
---------------------------------------------------------------------------------------

-- Head --
Stacktrace:
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:61)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:788)
    at org.lwjgl.opengl.DrawableGL.setPixelFormat(DrawableGL.java:61)
    at org.lwjgl.opengl.Display.create(Display.java:846)
    at org.lwjgl.opengl.Display.create(Display.java:757)
    at org.lwjgl.opengl.Display.create(Display.java:739)
    at ats.O(SourceFile:297)

-- Initialization --
Details:
Stacktrace:
    at ats.d(SourceFile:599)
    at net.minecraft.client.main.Main.main(SourceFile:101)

-- System Details --
Details:
    Minecraft Version: 1.6.2
    Operating System: Linux (i386) version 3.5.0-36-generic
    Java Version: 1.6.0_45, Sun Microsystems Inc.
    Java VM Version: Java HotSpot(TM) Client VM (mixed mode), Sun Microsystems Inc.
    Memory: 8700240 bytes (8 MB) / 26808320 bytes (25 MB) up to 518979584 bytes (494 MB)
    JVM Flags: 1 total; -Xmx512M
    AABB Pool Size: 0 (0 bytes; 0 MB) allocated, 0 (0 bytes; 0 MB) used
    Suspicious classes: No suspicious classes found.
    IntCache: cache: 0, tcache: 0, allocated: 0, tallocated: 0
    Launched Version: 1.6.2
    LWJGL: 2.9.0
    OpenGL: ~~ERROR~~ RuntimeException: No OpenGL context found in the current thread.
    Is Modded: Probably not. Jar signature remains and client brand is untouched.
    Type: Client (map_client.txt)
    Resource Pack: Default
    Current Language: ~~ERROR~~ NullPointerException: null
    Profiler Position: N/A (disabled)
    Vec3 Pool Size: ~~ERROR~~ NullPointerException: null

---

### Post by DeathByDenim on 2013-07-17
It sounds like the video drivers aren't loaded correctly. What graphics card do you use?
If it's an NVidia card, does [this thread]("http://ubuntuforums.org/showthread.php?t=1810956") help you?

---

### Post by LordFran on 2013-07-18
> **DeathByDenim said:**
> It sounds like the video drivers aren't loaded correctly. What graphics card do you use?
If it's an NVidia card, does [this thread]("http://ubuntuforums.org/showthread.php?t=1810956") help you?


I use a default Intel driver, and am not sure how to either update or change it

---

### Post by Mikeb85 on 2013-07-18
Download the current version of LWJGL, and replace the included LWJGL files which are found in the .minecraft/bin folder.  For some unknown reason, Minecraft seems to download a very old version of LWJGL when it installs itself the first time you fire up the JAR...

Intel video cards (the newish ones anyway) run Minecraft just fine BTW.

---

### Post by efflandt on 2013-07-18
The minecraft launcher for 1.6 versions no longer uses the old lwjgl 2.4.2 that earlier minecraft versions used by default. It automatically gets the most recent lwjgl as noted in the output for the error from minecraft 1.6.2, so I would not think that is the issue:> Launched Version: 1.6.2
    LWJGL: 2.9.0 But the only computer I have with Intel graphics is too old and slow to run minecraft effectively (laptop from 2006), so I cannot help with Intel related video issues.

You might also look through the minecraft forums [http://www.minecraftforum.net/forum](http://www.minecraftforum.net/forum) to see if anyone there knows or has suggestions about Intel video.

---

### Post by LordFran on 2013-07-19
> **efflandt said:**
> The minecraft launcher for 1.6 versions no longer uses the old lwjgl 2.4.2 that earlier minecraft versions used by default. It automatically gets the most recent lwjgl as noted in the output for the error from minecraft 1.6.2, so I would not think that is the issue: But the only computer I have with Intel graphics is too old and slow to run minecraft effectively (laptop from 2006), so I cannot help with Intel related video issues.

You might also look through the minecraft forums [http://www.minecraftforum.net/forum](http://www.minecraftforum.net/forum) to see if anyone there knows or has suggestions about Intel video.

I already have lwgjl updated

---

