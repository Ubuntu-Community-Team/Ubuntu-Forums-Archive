---
title: "Minecraft Black Screen fix?"
date: 2012-11-24
forum: Gaming &amp; Leisure
---

### Post by Jamie_Edwards on 2012-11-24
Hi guy's,

I know that this question has probably been asked many a time, but none of the solutions mentioned have worked.

When I launched the minecraft.jar file it launches normally, but when I log in the screen goes black.

Looking at one post it says that my might not have worked properly and trying to force update it will work, so I tried and... Nothing. Still the same outcome.

Any idea's on what else I could do? I'm quite annoyed that I've paid for a game that I can't even use properly.

Thanks.

---

### Post by Jamie_Edwards on 2012-11-24
While running it in terminal I get the following errors:

```

Exception in thread "Thread-3" java.lang.UnsatisfiedLinkError: /home/user/.minecraft/bin/natives/liblwjgl.so: /home/user/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary1(ClassLoader.java:1939)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1864)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1825)
	at java.lang.Runtime.load0(Runtime.java:792)
	at java.lang.System.load(System.java:1059)
	at org.lwjgl.Sys$1.run(Sys.java:69)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.Sys.doLoadLibrary(Sys.java:65)
	at org.lwjgl.Sys.loadLibrary(Sys.java:81)
	at org.lwjgl.Sys.<clinit>(Sys.java:98)
	at net.minecraft.client.Minecraft.F(SourceFile:1975)
	at asr.<init>(SourceFile:20)
	at net.minecraft.client.Minecraft.<init>(SourceFile:75)
	at asi.<init>(SourceFile:36)
	at net.minecraft.client.MinecraftApplet.init(SourceFile:36)
	at net.minecraft.Launcher.replace(Launcher.java:136)
	at net.minecraft.Launcher$1.run(Launcher.java:79)


```

Any ideas?

---

### Post by mentorious on 2012-11-24
Yeap, download [lwgjl libs]("http://downloads.sourceforge.net/project/java-game-lib/Official%20Releases/LWJGL%202.8.5/lwjgl-2.8.5.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fjava-game-lib%2Ffiles%2FOfficial%2520Releases%2FLWJGL%25202.8.5%2F&ts=1353779743&use_mirror=netcologne") and extract:

 jinput.jar, lwjgl.jar, lwjgl_util.jar from /linux/  in package to  your minecraft folder ~/.minecraft/bin.

Then extract libs from path 'linux/natives' to ~/.minecraft/bin/natives

Everything should working :) Save these files, you must replace libs after 
Minecraft update.

---

### Post by Majlo on 2012-11-24
Or you can use this script it's perfect .It will check current version and upgrade when needed.

[http://pastie.org/2194493]("http://pastie.org/2194493")

---

### Post by Gaygerbil on 2013-02-07
> **mentorious said:**
> Yeap, download [lwgjl libs]("http://downloads.sourceforge.net/project/java-game-lib/Official%20Releases/LWJGL%202.8.5/lwjgl-2.8.5.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fjava-game-lib%2Ffiles%2FOfficial%2520Releases%2FLWJGL%25202.8.5%2F&ts=1353779743&use_mirror=netcologne") and extract:

 jinput.jar, lwjgl.jar, lwjgl_util.jar from /linux/  in package to  your minecraft folder ~/.minecraft/bin.

Then extract libs from path 'linux/natives' to ~/.minecraft/bin/natives

Everything should working :) Save these files, you must replace libs after 
Minecraft update.

This worked for me, so thank you! :]

---

