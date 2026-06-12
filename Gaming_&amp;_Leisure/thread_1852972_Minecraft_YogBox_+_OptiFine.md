---
title: "Minecraft YogBox + OptiFine"
date: 2011-10-01
forum: Gaming &amp; Leisure
---

### Post by DaimyoKirby on 2011-10-01
Hi there.
I'm running Xubuntu 11.04.

I wanted to use the [YogBox]("http://yogiverse.com/showthread.php?11841-YogBox-A-carefully-chosen-compilation-of-good-mods") modpack, and I've checked this multiple times, and I always end with the same results:

1. I check to make sure vanilla Minecraft is working - it is.
2. I install the YogBox using the install, it successfully completes.
3. I check to make sure YogBox Minecraft is working - it is.
4. I paste all of the OptiFine_1.8.1_HD_S_A class files into minecraft.jar, and recompress it into a .jar file.
5. I check to make sure YogBox + OptiFine Minecraft it working - it isn't; It seems to be getting stuck at the splash screen, and when I have it run from terminal, this is what is happening:
```
17 achievements
161 recipes
Setting user: DaimyoKirby, 586902452901318104

OptiFine_1.8.1_HD_S
Sat Oct 01 10:15:11 EDT 2011
OS: Linux (i386) version 2.6.38-11-generic
Java: 1.6.0_22, Sun Microsystems Inc.
VM: OpenJDK Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
OpenGL: GeForce 7150M / nForce 630M/PCI/SSE2/3DNOW! version 2.1.2 NVIDIA 270.41.06, NVIDIA Corporation
OpenGL Version: 2.1
Exception in thread "Minecraft main thread" java.lang.NoClassDefFoundError: ModLoader
	at aam.<init>(aam.java:61)
	at aam.<clinit>(aam.java:10)
	at net.minecraft.client.Minecraft.a(SourceFile:259)
	at net.minecraft.client.Minecraft.run(SourceFile:629)
	at java.lang.Thread.run(Thread.java:679)
Caused by: java.lang.ClassNotFoundException: ModLoader
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	... 5 more


```

Does anyone know what's wrong?
Does anyone know how to fix this?

---

### Post by cynt_ on 2011-10-01
Does it work vanilla but with optifine?
Did you try modloader?

---

### Post by DaimyoKirby on 2011-10-01
Yes, vanilla worked with optifine.
After refreshing my .minecraft folder, with a fresh minecraft.jar, I tried installing Nature Overhaul, which also required ModLoader and ModOptionsAPI.
This was the output:
```
17 achievements
161 recipes
Setting user: DaimyoKirby, 294592328990227359
Exception in thread "Minecraft main thread" java.lang.NoClassDefFoundError: ModLoader
	at aam.<init>(aam.java:61)
	at aam.<clinit>(aam.java:10)
	at net.minecraft.client.Minecraft.a(SourceFile:259)
	at net.minecraft.client.Minecraft.run(SourceFile:629)
	at java.lang.Thread.run(Thread.java:679)
Caused by: java.lang.ClassNotFoundException: ModLoader
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	... 5 more
```

---

### Post by DaimyoKirby on 2011-10-03
I found why it wasn't working.

For some reason, when modloader is installed (either by installer or manually), it puts modloader.class into /java/lang in your minecraft.jar, enabling Modloader useless.

If you move this out of /java/lang, and into the area in minecraft.jar where the other .class files are, it should work properly.

---

### Post by OpenJacob on 2011-10-03
Glad it works, I had another problem with the same results with an old mod.

---

### Post by Yuffie yamamoto on 2011-12-21
Hi I know this has been solved already but I was wondering if you could help me with my problem since this thread seems to be the only yogbox related one. What settings are you using for minecraft.

No matter what I do I hit either a black screen or crash when I even breath the word mod into my minecraft.
I was thinking it might just be the settings I am playing in like maybe I have the wrong java or I need to update or something. I'd really appreciate it.

---

