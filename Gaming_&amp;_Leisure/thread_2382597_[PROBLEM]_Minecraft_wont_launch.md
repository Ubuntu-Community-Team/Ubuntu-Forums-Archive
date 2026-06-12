---
title: "[PROBLEM] Minecraft wont launch"
date: 2018-01-15
forum: Gaming &amp; Leisure
---

### Post by theredsf on 2018-01-15
Ive recently installed minecraft for linux ubuntu on my chomebook (dual-booting) and ive installed it comepletely but it wont launch for some reason...
I get this error in my logs:
Java HotSpot(TM) Server VM warning: Using incremental CMS is deprecated and will likely be removed in a future release
Java HotSpot(TM) Server VM warning: You have loaded library /home/derp/.minecraft/versions/1.12.2/1.12.2-natives-66480330985531/liblwjgl64.so which might have disabled stack guard. The VM will try to fix the stack guard now.
It's highly recommended that you fix the library with 'execstack -c <libfile>', or link it with '-z noexecstack'.
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/derp/.minecraft/versions/1.12.2/1.12.2-natives-66480330985531/liblwjgl.so: /home/derp/.minecraft/versions/1.12.2/1.12.2-natives-66480330985531/liblwjgl.so: cannot open shared object file: No such file or directory (Possible cause: can't load IA 32-bit .so on a ARM-bit platform)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1941)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1857)
	at java.lang.Runtime.loadLibrary0(Runtime.java:870)
	at java.lang.System.loadLibrary(System.java:1122)
	at org.lwjgl.Sys$1.run(Sys.java:72)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.Sys.doLoadLibrary(Sys.java:66)
	at org.lwjgl.Sys.loadLibrary(Sys.java:96)
	at org.lwjgl.Sys.<clinit>(Sys.java:117)
	at bib.I(SourceFile:2825)
	at net.minecraft.client.main.Main.main(SourceFile:38)
I dont understant the java IDE language so hopefully someone does.
Im on Linux32 Ubuntu (version unclear) i think 13.03

---

### Post by theredsf on 2018-01-15
Ive installed execstack

---

### Post by Perfect Storm on 2018-01-15
This may be the problem:
```
/liblwjgl.so: /home/derp/.minecraft/versions/1.12.2/1.12.2-natives-66480330985531/liblwjgl.so: **cannot open shared object file: No such file or directory (Possible cause: can't load IA 32-bit .so on a ARM-bit platform)**
```

---

