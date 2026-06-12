---
title: "Minecraft"
date: 2017-01-02
forum: Gaming &amp; Leisure
---

### Post by Timecraftian on 2017-01-02
Hi,

Everytime i try to launch minecraft i get an error message.

---- Minecraft Crash Report ----
// Don't be sad. I'll do better next time, I promise!

Time: 1/2/17 5:07 PM
Description: Initializing game

java.lang.ExceptionInInitializerError
    at bes.ar(SourceFile:626)
    at bes.an(SourceFile:434)
    at bes.a(SourceFile:383)
    at net.minecraft.client.main.Main.main(SourceFile:124)
Caused by: java.lang.ArrayIndexOutOfBoundsException: 0
    at org.lwjgl.opengl.LinuxDisplay.getAvailableDisplayModes(LinuxDisplay.java:951)
    at org.lwjgl.opengl.LinuxDisplay.init(LinuxDisplay.java:738)
    at org.lwjgl.opengl.Display.<clinit>(Display.java:138)
    ... 4 more


A detailed walkthrough of the error, its code path and all known details is as follows:
---------------------------------------------------------------------------------------

-- Head --
Thread: Client thread
Stacktrace:
    at bes.ar(SourceFile:626)
    at bes.an(SourceFile:434)

-- Initialization --
Details:
Stacktrace:
    at bes.a(SourceFile:383)
    at net.minecraft.client.main.Main.main(SourceFile:124)

-- System Details --
Details:
    Minecraft Version: 1.11.2
    Operating System: Linux (amd64) version 4.4.0-21-generic
    Java Version: 1.8.0_111, Oracle Corporation
    Java VM Version: OpenJDK 64-Bit Server VM (mixed mode), Oracle Corporation
    Memory: 35016328 bytes (33 MB) / 150994944 bytes (144 MB) up to 2102919168 bytes (2005 MB)
    JVM Flags: 2 total; -Xmx2G -Xmn128M
    IntCache: cache: 0, tcache: 0, allocated: 0, tallocated: 0
    Launched Version: 1.11.2
    LWJGL: 2.9.4
    OpenGL: ~~ERROR~~ RuntimeException: No OpenGL context found in the current thread.
    GL Caps: 
    Using VBOs: Yes
    Is Modded: Probably not. Jar signature remains and client brand is untouched.
    Type: Client (map_client.txt)
    Resource Packs: 
    Current Language: ~~ERROR~~ NullPointerException: null
    Profiler Position: N/A (disabled)
    CPU: <unknown>


I have searched through multiple threads and couldnt find a solution.

(And yes i am new to ubuntu)

---

### Post by uNoubu8a on 2017-01-04
Hi,

[From this thread]("https://bbs.archlinux.org/viewtopic.php?id=184190") it seems it may be due to hybrid graphics (as I have no idea what hardware you have it is difficult to judge if this is applicable to you).  Secondly people have had success getting past "OpenGL: ~~ERROR~~ RuntimeException: No OpenGL context found in the current thread." this error by installing xorg-xrandr (but I am not close to an Ubuntu machine to see what the package for Ubuntu would be and if it is even applicable).

---

### Post by sgian on 2017-01-06
I agree that it is possibly a driver problem,  If you are not using proprietary drivers, try installing them and see if that works.  Some more information on the pc could be useful, like version of Ubuntu, RAM, CPU, graphics card, and what graphics driver you are using.

---

### Post by Bucky Ball on 2017-01-06
> **sgian said:**
> Some more information on the pc could be useful, like version of Ubuntu, RAM, CPU, graphics card, and what graphics driver you are using.

+1. Welcome. And changing the thread title to something that accurately describes your actual issue will help you get more support (Edit Post> Go Advanced). :) Good luck.

---

