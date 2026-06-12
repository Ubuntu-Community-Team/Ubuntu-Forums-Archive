---
title: "Minecraft Crash"
date: 2014-02-01
forum: Gaming &amp; Leisure
---

### Post by eliaswibz on 2014-02-01
Hi all.

I get an error after the launcher updates the game.
 
I have tried this:
 [http://askubuntu.com/questions/225432/how-to-correctly-install-and-troubleshoot-minecraft-client](http://askubuntu.com/questions/225432/how-to-correctly-install-and-troubleshoot-minecraft-client)
and this:
[http://askubuntu.com/questions/300511/cant-run-minecraft-a-glx-problem](http://askubuntu.com/questions/300511/cant-run-minecraft-a-glx-problem)

But it doesn't work.

This is the crash report:

```

Description: Initializing game


org.lwjgl.LWJGLException: Could not init GLX
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:61)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:818)
    at org.lwjgl.opengl.DrawableGL.setPixelFormat(DrawableGL.java:61)
    at org.lwjgl.opengl.Display.create(Display.java:846)
    at org.lwjgl.opengl.Display.create(Display.java:757)
    at org.lwjgl.opengl.Display.create(Display.java:739)
    at azi.ad(SourceFile:325)
    at azi.f(SourceFile:696)
    at net.minecraft.client.main.Main.main(SourceFile:152)




A detailed walkthrough of the error, its code path and all known details is as follows:
---------------------------------------------------------------------------------------


-- Head --
Stacktrace:
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:61)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:818)
    at org.lwjgl.opengl.DrawableGL.setPixelFormat(DrawableGL.java:61)
    at org.lwjgl.opengl.Display.create(Display.java:846)
    at org.lwjgl.opengl.Display.create(Display.java:757)
    at org.lwjgl.opengl.Display.create(Display.java:739)
    at azi.ad(SourceFile:325)


-- Initialization --
Details:
Stacktrace:
    at azi.f(SourceFile:696)
    at net.minecraft.client.main.Main.main(SourceFile:152)


-- System Details --
Details:
    Minecraft Version: 1.7.4
    Operating System: Linux (amd64) version 3.5.0-45-generic
    Java Version: 1.7.0_45, Oracle Corporation
    Java VM Version: Java HotSpot(TM) 64-Bit Server VM (mixed mode), Oracle Corporation
    Memory: 33374776 bytes (31 MB) / 76021760 bytes (72 MB) up to 954728448 bytes (910 MB)
    JVM Flags: 1 total; -Xmx1G
    AABB Pool Size: 0 (0 bytes; 0 MB) allocated, 0 (0 bytes; 0 MB) used
    IntCache: cache: 0, tcache: 0, allocated: 0, tallocated: 0
    Launched Version: 1.7.4
    LWJGL: 2.9.1
    OpenGL: ~~ERROR~~ RuntimeException: No OpenGL context found in the current thread.
    GL Caps: 
    Is Modded: Probably not. Jar signature remains and client brand is untouched.
    Type: Client (map_client.txt)
    Resource Packs: []
    Current Language: ~~ERROR~~ NullPointerException: null
    Profiler Position: N/A (disabled)
    Vec3 Pool Size: ~~ERROR~~ NullPointerException: null
    Anisotropic Filtering: Off (1)


``` 

This is what I get when I do as it is said here: [http://ubuntuforums.org/showthread.php?t=1810956](http://ubuntuforums.org/showthread.php?t=1810956)

```

elias@EquipoEliasUbuntu:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 635M] (rev a1)



elias@EquipoEliasUbuntu:~$ dmesg |grep NVIDIA
[   30.497949] nvidia: module license 'NVIDIA' taints kernel.
[   30.506158] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.116  Mon Oct 28 20:39:03 PDT 2013



elias@EquipoEliasUbuntu:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".



elias@EquipoEliasUbuntu:~$ cat /etc/X11/xorg.conf


Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection


Section "Screen"
Identifier      "Default Screen"
DefaultDepth    24
EndSection


Section "Module"
Load    "glx"
EndSection


Section "Device"
Identifier      "Default Device"
Driver  "nvidia"
Option  "NoLogo"        "True"
EndSection

```


Hopefully someone can help me with this, I would extremely appreciate it.

Thanks,

Eldar

---

### Post by PotatoHead007 on 2014-02-01
He[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1901878")y Eldar :)

I play Minecraft on Ubuntu 12.04.3, 32bit. I never have a problem with updating, but i think i may know what your problem is.

Do you have any mods installed? Even Optifine can crash your update. 
Try completely deleting Minecraft(but keep your "saves" folder), then reinstall it, and paste your "saves" folder back in. This will give you a fresh install of Minecraft, while at the same time saving your worlds.
Also, make sure you have installed the nvidia driver for your graphics card. Here is a link to the drivers: [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
**Make sure you select the right driver! **Failing to do so may render your Ubuntu useless, and trying to undo the damage is difficult. So be careful if you go down that path.

If that does not resolve the issue, plase post the error output again :D

---

### Post by efflandt on 2014-02-04
I imagine you do not have something set up properly for the dual Intel/Nvidia graphics or bumblebee. When I got a laptop with Intel HD 4600 and Nvidia GTX 765M, I heard that 13.10 had better support for the dual graphics than earlier Ubuntu versions, so I used that. My xorg.conf is totally empty. Maybe yours is confusing X trying to use nvidia glx for default Intel graphics. The power LED on my laptop is blue when using Intel and amber when using Nvidia graphics.

With bumblebee, preceding a command with **optirun** uses Nvidia graphics instead of default Intel. When everything is working properly, either **glxinfo | grep direct** or **optirun glxinfo | grep direct** should return **direct rendering: Yes**

In 64-bit 13.10 with nvidia drivers installed and openjdk7-jre it launches and runs fine with nvidia graphics by using: optirun java -jar Minecraft.jar

And it runs without optirun using default Intel graphics, although, I have not had a chance to test frame rate.

---

