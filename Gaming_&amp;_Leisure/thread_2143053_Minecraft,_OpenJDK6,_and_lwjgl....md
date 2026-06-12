---
title: "Minecraft, OpenJDK6, and lwjgl..."
date: 2013-05-07
forum: Gaming &amp; Leisure
---

### Post by derklempner on 2013-05-07
I'm having the "sticking keys" issue running Minecraft (loading with MagicLauncher) with OpenJDK6:
```
me@my_computer:~$ java -version
java version "1.6.0_27"
OpenJDK Runtime Environment (IcedTea6 1.12.3) (6b27-1.12.3-0ubuntu1~12.04.1)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)
```
I updated **lwjgl** to various different versions from 2.6 all the way up to 2.9.0. Every time I update with **lwjgl**, I get the following errors in the log file from MagicLauncher:
```
*** MagicMinecraftLauncher 1.0.0 ***
Disable inactive mods
java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at magic.launcher.Launcher.main(Unknown Source)
Caused by: java.lang.UnsatisfiedLinkError: org.lwjgl.DefaultSysImplementation.getPointerSize()I
    at org.lwjgl.DefaultSysImplementation.getPointerSize(Native Method)
    at org.lwjgl.Sys.<clinit>(Sys.java:100)
    at net.minecraft.client.Minecraft.G(SourceFile:1985)
    at net.minecraft.client.Minecraft.main(SourceFile:1559)
    ... 5 more

```

Now when I attempt to just run Minecraft without loading it from MagicLauncher, the window goes black and the output from the command prompt is as follows:
```
me@my_computer:~$ java -jar minecraft.jar 
asdf
Exception in thread "Thread-5" java.lang.UnsatisfiedLinkError: org.lwjgl.DefaultSysImplementation.getPointerSize()I
	at org.lwjgl.DefaultSysImplementation.getPointerSize(Native Method)
	at org.lwjgl.Sys.<clinit>(Sys.java:100)
	at net.minecraft.client.Minecraft.G(SourceFile:1985)
	at awe.<init>(SourceFile:20)
	at net.minecraft.client.Minecraft.<init>(SourceFile:76)
	at avv.<init>(SourceFile:38)
	at net.minecraft.client.MinecraftApplet.init(SourceFile:38)
	at net.minecraft.Launcher.replace(Launcher.java:136)
	at net.minecraft.Launcher$1.run(Launcher.java:79)

```

I'm running this on 64-bit Ubuntu 12.04 with Nvidia proprietary drivers. If I start the game without updating **lwjgl**, it runs fine -- except for the sticking keys.

Is this an issue with OpenJDK, **lwjgl**, Minecraft, or my video driver? Is there a way to get around this, even if it means using Oracle Java 6 or 7?

---

### Post by derklempner on 2013-05-07
I decided to switch to OpenJDK 7, but the same problem persists.

---

### Post by Horbo on 2013-05-08
MC doesn't like Oracle Java 7 (black screen on load, usually).  Install and run with Oracle Java 6.


[COLOR=#000000][FONT=Verdana]sudo add-apt-repository ppa:webupd8team/java
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]sudo apt-get update && sudo apt-get install oracle-java6-installer[/FONT][/COLOR]

---

### Post by efflandt on 2013-05-10
Minecraft works fine with openjdk 6 or 7 jre, and I have been using lwjgl 2.6 for a long time, since I had the sticky key issue with 2.4.2 included with minecraft.

Maybe you are not putting the proper lwjgl files in the proper places.

**jinput.jar**, **lwjgl.jar** and **lwjgl_util.jar** go into **~/.minecraft/bin** and the 6 files from the **natives/linux/** directory of the zip file go into **~/.minecraft/bin/natives/** (without the linux dir).

---

### Post by derklempner on 2013-05-10
> **efflandt said:**
> Minecraft works fine with openjdk 6 or 7 jre, and I have been using lwjgl 2.6 for a long time, since I had the sticky key issue with 2.4.2 included with minecraft.

Maybe you are not putting the proper lwjgl files in the proper places.

**jinput.jar**, **lwjgl.jar** and **lwjgl_util.jar** go into **~/.minecraft/bin** and the 6 files from the **natives/linux/** directory of the zip file go into **~/.minecraft/bin/natives/** (without the linux dir).
Yes, those are the files I'm replacing. I know I've got the right files, I know I've got the right versions of OpenJDK, but I don't know why it crashes when I install **lwjgl-2.6** -- or any other version of **lwjgl**. This is why I'm thinking it may be a video driver issue; I'm using an Nvidia GeForce GT 520 with the proprietary drivers (not *nouveau*).

---

### Post by derklempner on 2013-05-10
> **Horbo said:**
> MC doesn't like Oracle Java 7 (black screen on load, usually).  Install and run with Oracle Java 6.


[COLOR=#000000][FONT=Verdana]sudo add-apt-repository ppa:webupd8team/java
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]sudo apt-get update && sudo apt-get install oracle-java6-installer[/FONT][/COLOR]
Thanks, but I'm not running Oracle Java 7. Or Oracle Java 6. I'm using OpenJDK 6 and 7.

---

### Post by Horbo on 2013-05-11
> **derklempner said:**
> Thanks, but I'm not running Oracle Java 7. Or Oracle Java 6. I'm using OpenJDK 6 and 7.

I can see that.  You asked for a solution "[COLOR=#000000]even if it means using Oracle Java 6 or 7?"  

I think I've provided one: use Oracle Java 6 (but don't use 7).[/COLOR]

---

### Post by derklempner on 2013-05-13
> **Horbo said:**
> I can see that.  You asked for a solution "[COLOR=#000000]even if it means using Oracle Java 6 or 7?"  

I think I've provided one: use Oracle Java 6 (but don't use 7).[/COLOR]
Sorry. I tried Oracle Java. Same issue.

I think it has to do with my video driver, because I'm running Minecraft on other computers running Ubuntu 12.04 and 13.04, both with Intel video cards and using OpenJDK and Oracle Java. No issue with sticking keys.

This makes me think the video card is the difference maker, because that's the only difference between the systems I can reconcile. 32-bit vs. 64-bit may also be an issue, but i can't imagine that's the problem since the only real hardware difference is the video cards and the only problem I seem to have is with Minecraft. Is there an known problem with Nvidia drivers and Java issues?

---

### Post by efflandt on 2013-05-13
These are the lwjgl 2.6 files I have been using for minecraft since at least Ubuntu 10.10, then 11.10, and now 12.04 (all 64-bit) with openjdk-6-jre originally, and openjdk-7-jre more recently (due to one minecraft mod in a tekkit server requiring 7). Not sure when I actually installed the files, because the Oct 2010 date is the date of the files in the lwjgl-2.6.zip file. I simply copied the entire .minecraft directory over to newer Ubuntu versions (or to my tablet PC which still has openjdk-6-jre).
```
efflandt@xps8100-1204:~$ ls -l ~/.minecraft/bin/jin* ~/.minecraft/bin/*gl*
-rw-r--r-- 1 efflandt efflandt 214859 Oct 18  2010 /home/efflandt/.minecraft/bin/jinput.jar
-rw-r--r-- 1 efflandt efflandt 867028 Oct 18  2010 /home/efflandt/.minecraft/bin/lwjgl.jar
-rw-r--r-- 1 efflandt efflandt 127598 Oct 18  2010 /home/efflandt/.minecraft/bin/lwjgl_util.jar
efflandt@xps8100-1204:~$ ls -l ~/.minecraft/bin/natives
total 1488
-rw-r--r-- 1 efflandt efflandt  14512 Oct 18  2010 libjinput-linux64.so
-rw-r--r-- 1 efflandt efflandt  13824 Oct 18  2010 libjinput-linux.so
-rw-r--r-- 1 efflandt efflandt 508936 Oct 18  2010 liblwjgl64.so
-rw-r--r-- 1 efflandt efflandt 374744 Oct 18  2010 liblwjgl.so
-rw-r--r-- 1 efflandt efflandt 304661 Oct 18  2010 libopenal64.so
-rw-r--r-- 1 efflandt efflandt 292803 Oct 18  2010 libopenal.so
```I have run minecraft in various nvidia driver versions since at least 295 something or maybe earlier.  I am currently running nvidia-experimental-310 (310.14) because that is what Steam recommends.

When my GT 430 began failing, the symptoms in Linux were that the keyboard and mouse buttons stopped responding (effectively freezing any input) while the mouse cursor usually still moved.  Although, that happened randomly in the desktop, rarely in minecraft. And Win7 would occasionally freeze for awhile and say "The video driver stopped responding, recovered", until eventually it could not recover. When it got to the point that Linux often would not boot due to lack of video card response, I replaced it with GTX 550 Ti which has never had any issues. So I don't imagine that your GT 520 would have nvidia driver support issues.

Note that when I played tekkit (which at that time was still minecraft 1.2.5 with a bunch of mods) if I tried to change the lwjgl version it used, it would change it back to the default version 2.4.2, so I would occasionally get stuck movement keys.

---

### Post by derklempner on 2013-05-13
> **efflandt said:**
> These are the lwjgl 2.6 files I have been using for minecraft since at least Ubuntu 10.10, then 11.10, and now 12.04 (all 64-bit) with openjdk-6-jre originally, and openjdk-7-jre more recently (due to one minecraft mod in a tekkit server requiring 7). Not sure when I actually installed the files, because the Oct 2010 date is the date of the files in the lwjgl-2.6.zip file. I simply copied the entire .minecraft directory over to newer Ubuntu versions (or to my tablet PC which still has openjdk-6-jre).
```
efflandt@xps8100-1204:~$ ls -l ~/.minecraft/bin/jin* ~/.minecraft/bin/*gl*
-rw-r--r-- 1 efflandt efflandt 214859 Oct 18  2010 /home/efflandt/.minecraft/bin/jinput.jar
-rw-r--r-- 1 efflandt efflandt 867028 Oct 18  2010 /home/efflandt/.minecraft/bin/lwjgl.jar
-rw-r--r-- 1 efflandt efflandt 127598 Oct 18  2010 /home/efflandt/.minecraft/bin/lwjgl_util.jar
efflandt@xps8100-1204:~$ ls -l ~/.minecraft/bin/natives
total 1488
-rw-r--r-- 1 efflandt efflandt  14512 Oct 18  2010 libjinput-linux64.so
-rw-r--r-- 1 efflandt efflandt  13824 Oct 18  2010 libjinput-linux.so
-rw-r--r-- 1 efflandt efflandt 508936 Oct 18  2010 liblwjgl64.so
-rw-r--r-- 1 efflandt efflandt 374744 Oct 18  2010 liblwjgl.so
-rw-r--r-- 1 efflandt efflandt 304661 Oct 18  2010 libopenal64.so
-rw-r--r-- 1 efflandt efflandt 292803 Oct 18  2010 libopenal.so
```
Yep, those are the exact same files I use, but Minecraft just crashes when I replace them and try to start the game.

I have no idea what the Java errors mean, so I was hoping somebody here would be able to give me some insight or assistance. I'm sure I can't be the only person having this issue, but extensive Google searches have turned up nothing.

---

### Post by derklempner on 2013-05-13
Crap, I just realized the directory I was storing the **natives** files in was actually named **native**. Hopefully, that's the issue, but I won't be able to try it out until an hour from now...

---

### Post by derklempner on 2013-05-13
Go figure. #-o

---

