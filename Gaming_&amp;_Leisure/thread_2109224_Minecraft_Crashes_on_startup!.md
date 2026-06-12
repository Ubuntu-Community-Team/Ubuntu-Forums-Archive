---
title: "Minecraft Crashes on startup!"
date: 2013-01-26
forum: Gaming &amp; Leisure
---

### Post by Champlin93 on 2013-01-26
I've been playing Minecraft up till now with no problems but just today when I tried to log into Minecraft I just got a black window. So I tried again with Magic Launcher and I got this crash report:

```
*** MagicMinecraftLauncher 1.0.0 ***
Disable inactive mods
java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:601)
    at magic.launcher.Launcher.main(Unknown Source)
Caused by: java.lang.UnsatisfiedLinkError: /home/josh/.minecraft/bin/natives/liblwjgl.so: /home/josh/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary1(ClassLoader.java:1939)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1864)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1854)
    at java.lang.Runtime.loadLibrary0(Runtime.java:845)
    at java.lang.System.loadLibrary(System.java:1084)
    at org.lwjgl.Sys$1.run(Sys.java:72)
    at java.security.AccessController.doPrivileged(Native Method)
    at org.lwjgl.Sys.doLoadLibrary(Sys.java:65)
    at org.lwjgl.Sys.loadLibrary(Sys.java:81)
    at org.lwjgl.Sys.<clinit>(Sys.java:98)
    at net.minecraft.client.Minecraft.F(SourceFile:1976)
    at net.minecraft.client.Minecraft.main(SourceFile:1564)
    ... 5 more

```

I also tried launching via terminal:

```
~$ java -jar /home/josh/.minecraft/minecraft.jar
asdf
Exception in thread "Thread-3" java.lang.UnsatisfiedLinkError: /home/josh/.minecraft/bin/natives/liblwjgl.so: /home/josh/.minecraft/bin/natives/liblwjgl.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
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
	at net.minecraft.client.Minecraft.F(SourceFile:1976)
	at asz.<init>(SourceFile:20)
	at net.minecraft.client.Minecraft.<init>(SourceFile:75)
	at asq.<init>(SourceFile:38)
	at net.minecraft.client.MinecraftApplet.init(SourceFile:38)
	at net.minecraft.Launcher.replace(Launcher.java:136)
	at net.minecraft.Launcher$1.run(Launcher.java:79)

```

Since both my Minecraft Server and Magic Launcher work fine it seems like its something wrong with Minecraft but i tried the "force update" option in the log in menu to no avail.

PLEASE HELP I'M ADDICTED TO THIS GAME!!

---

### Post by efflandt on 2013-01-27
Did you change or update your **lwjgl** version lately and maybe not get all the files switched over? There should be files in that directory for 32 and 64-bit and it sounds you are running 64-bit Linux, but only have those 32-bit files.

```
efflandt@XPS8100-1204:~$ ls .minecraft/bin/natives
libjinput-linux64.so  liblwjgl64.so  libopenal64.so
libjinput-linux.so    liblwjgl.so    libopenal.so
```

---

### Post by meteorrock on 2013-01-27
Does Minecraft use flash to play on the internet? 

If so I got this solution over in this thread here if you want to take a look. [http://ubuntuforums.org/showthread.php?t=2108573](http://ubuntuforums.org/showthread.php?t=2108573)

There are some other links that go outside of that thread in the forums here. They show you how to get flash working for Java if you want.

---

