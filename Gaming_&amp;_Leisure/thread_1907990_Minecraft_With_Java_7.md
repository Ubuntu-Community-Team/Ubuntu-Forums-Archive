---
title: "Minecraft With Java 7"
date: 2012-01-12
forum: Gaming &amp; Leisure
---

### Post by Kodeine on 2012-01-12
Salutations!

So I installed the oracle java 7 packages and are currently trying to get minecraft to come on. I've been having some trouble with MC latley due to my Intel messa drivers. Dots appear of some of the textures in the game. I wanted to try out java 7 to see if one, the dots went away and two, if there was any performance gains. When I run minecraft this is what I get.

```
zack@LinuxDesktop:~/.minecraft$  java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
Hello!
URL: file:/home/zack/.minecraft/bin/lwjgl.jar
URL: file:/home/zack/.minecraft/bin/jinput.jar
URL: file:/home/zack/.minecraft/bin/lwjgl_util.jar
URL: file:/home/zack/.minecraft/bin/minecraft.jar
URL: file:/home/zack/.minecraft/bin/linux_natives.jar
27 achievements
174 recipes
Setting user: KoopaTroopa, 12345
Exception in thread "Minecraft main thread" java.lang.UnsatisfiedLinkError: /home/zack/.minecraft/bin/natives/liblwjgl.so: libjawt.so: cannot open shared object file: No such file or directory
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1928)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1825)
	at java.lang.Runtime.load0(Runtime.java:792)
	at java.lang.System.load(System.java:1059)
	at org.lwjgl.Sys$1.run(Sys.java:69)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.Sys.doLoadLibrary(Sys.java:65)
	at org.lwjgl.Sys.loadLibrary(Sys.java:81)
	at org.lwjgl.Sys.<clinit>(Sys.java:98)
	at org.lwjgl.opengl.Display.<clinit>(Display.java:132)
	at net.minecraft.client.Minecraft.a(SourceFile:187)
	at net.minecraft.client.Minecraft.run(SourceFile:644)
	at java.lang.Thread.run(Thread.java:722)
```

---

### Post by ergo-proxy on 2012-01-13
Before launching minecraft onusing jav7 you need to export ld_library_path:
 
export LD_LIBRARY_PATH=/opt/java/jre/lib/amd64 (the path might be different if you use non 64bit java, so change amd64 to i386 afair)

---

### Post by Perfect Storm on 2012-01-13
I nice and with good explanation on how to set up Oracle Java correctly on Ubuntu; [https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

