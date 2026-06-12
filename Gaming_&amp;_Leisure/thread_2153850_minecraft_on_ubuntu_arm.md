---
title: "minecraft on ubuntu arm"
date: 2013-06-12
forum: Gaming &amp; Leisure
---

### Post by kirby2ig on 2013-06-12
Okay, does anyone know how one would get minecraft to work on ubuntu arm? I am on a samsung chromebook running ubuntu 12.04. It might be possible if i compile lwjgl for opengl-es, but I don't know how to do that. Anyone have any suggestions?


EDIT:
Okay, so I researched compiling lwjgl for arm and found this [http://www.raspberrypi.org/phpBB3/viewtopic.php?f=34&t=19532](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=34&t=19532). Using this, I wasable to get this far:
$ java -Xmx1024M -Xmx1024M -jar '/home/user/Desktop/minecraft (1).jar' 


(process:3259): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
asdf
229 recipes
27 achievements
2013-06-12 17:50:02 [CLIENT] [INFO] Setting user: kirby2ig
(Session ID is ff30bbadd70524bedd7f208d32606bc3fb34d589)
2013-06-12 17:50:02 [CLIENT] [INFO] LWJGL Version: 2.8.1
Exception in thread "Minecraft main thread" java.lang.UnsatisfiedLinkError: org.lwjgl.opengl.GLContext.ngetFunctionAddress(J)J
	at org.lwjgl.opengl.GLContext.ngetFunctionAddress(Native Method)
	at org.lwjgl.opengl.GLContext.getFunctionAddress(GLContext.java:195)
	at org.lwjgl.opengl.ContextCapabilities.initAllStubs(ContextCapabilities.java:4958)
	at org.lwjgl.opengl.ContextCapabilities.<init>(ContextCapabilities.java:5322)
	at org.lwjgl.opengl.GLContext.useContext(GLContext.java:355)
	at org.lwjgl.opengl.ContextGL.makeCurrent(ContextGL.java:195)
	at org.lwjgl.opengl.DrawableGL.makeCurrent(DrawableGL.java:110)
	at org.lwjgl.opengl.Display.makeCurrent(Display.java:731)
	at org.lwjgl.opengl.Display.makeCurrentAndSetSwapInterval(Display.java:1050)
	at org.lwjgl.opengl.Display.create(Display.java:877)
	at org.lwjgl.opengl.Display.create(Display.java:782)
	at net.minecraft.client.Minecraft.a(SourceFile:226)
	at avv.a(SourceFile:56)
	at net.minecraft.client.Minecraft.run(SourceFile:507)
	at java.lang.Thread.run(Thread.java:679)


Any idea on how to fix this error?

---

### Post by kirby2ig on 2013-06-14
Okay, so I ran sudo apt-get install liblwjgl-java liblwjgl-java-doc liblwjgl-jni. Using these .so and .jar files, I was able to get minecraft to get to the title screen, but now I have another problem. Minecraft is running unusually slow. Does anyone know how to give java accelerated graphics on an arm chromebook? Also sound doesn't work. Anyone know how I can fix that?

---

