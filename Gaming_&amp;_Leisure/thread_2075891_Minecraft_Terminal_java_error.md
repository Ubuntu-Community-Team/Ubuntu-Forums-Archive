---
title: "Minecraft Terminal java error"
date: 2012-10-24
forum: Gaming &amp; Leisure
---

### Post by blk59801 on 2012-10-24
Hey, i have been trying to play minecraft with more ram because it is slow with the regular amount i have but i want more. the error is below
[B]asdf
Exception in thread "Thread-3" java.lang.UnsatisfiedLinkError: /home/blake/.minecraft/bin/natives/liblwjgl.so: libjawt.so: cannot open shared object file: No such file or directory
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary1(Unknown Source)
    at java.lang.ClassLoader.loadLibrary0(Unknown Source)
    at java.lang.ClassLoader.loadLibrary(Unknown Source)
    at java.lang.Runtime.load0(Unknown Source)
    at java.lang.System.load(Unknown Source)
    at org.lwjgl.Sys$1.run(Sys.java:69)
    at java.security.AccessController.doPrivileged(Native Method)
    at org.lwjgl.Sys.doLoadLibrary(Sys.java:65)
    at org.lwjgl.Sys.loadLibrary(Sys.java:81)
    at org.lwjgl.Sys.<clinit>(Sys.java:98)
    at net.minecraft.client.Minecraft.F(SourceFile:1857)
    at aof.<init>(SourceFile:20)
    at net.minecraft.client.Minecraft.<init>(SourceFile:77)
    at anw.<init>(SourceFile:36)
    at net.minecraft.client.MinecraftApplet.init(SourceFile:36)
    at net.minecraft.Launcher.replace(Launcher.java:136)
    at net.minecraft.Launcher$1.run(Launcher.java:79)
[/B]

---

### Post by sir.sargento on 2012-10-24
From what I can tell it is looking for **liblwjgl.so **which it says should be located in ** /home/blake/.minecraft/bin/natives/. **I could be wrong but I would start with googling that error. I will do the same and hopefully be able to help you out. I've never played minecraft but maybe I'll be useful.

EDIT: Try this [http://askubuntu.com/questions/171991/cant-get-minecraft-to-run-on-ubuntu](http://askubuntu.com/questions/171991/cant-get-minecraft-to-run-on-ubuntu) link out.

Tony

---

### Post by blk59801 on 2012-10-24
Had to modify the command a bit but i have it fixed, thank you

---

