---
title: "Minecraft crashes on launch"
date: 2014-04-11
forum: Gaming &amp; Leisure
---

### Post by daniel_k2 on 2014-04-11
Minecraft crashes on launch. I never see the menu screen, it happens right after I press play.

```
---- Minecraft Crash Report ----// This doesn't make any sense!


Time: 11/04/14 4:26 PM
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
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:622)
	at net.minecraft.launchwrapper.Launch.launch(Launch.java:131)
	at net.minecraft.launchwrapper.Launch.main(Launch.java:27)




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
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:622)
	at net.minecraft.launchwrapper.Launch.launch(Launch.java:131)
	at net.minecraft.launchwrapper.Launch.main(Launch.java:27)


-- System Details --
Details:
	Minecraft Version: 1.7.4
	Operating System: Linux (amd64) version 3.11.0-19-generic
	Java Version: 1.6.0_30, Sun Microsystems Inc.
	Java VM Version: OpenJDK 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
	Memory: 41991608 bytes (40 MB) / 74383360 bytes (70 MB) up to 954466304 bytes (910 MB)
	JVM Flags: 1 total; -Xmx1G
	AABB Pool Size: 0 (0 bytes; 0 MB) allocated, 0 (0 bytes; 0 MB) used
	IntCache: cache: 0, tcache: 0, allocated: 0, tallocated: 0
	Launched Version: 1.7.4-OptiFine_HD_D1
	LWJGL: 2.9.1
	OpenGL: ~~ERROR~~ RuntimeException: No OpenGL context found in the current thread.
	GL Caps: 
	Is Modded: Very likely; Jar signature invalidated
	Type: Client (map_client.txt)
	Resource Packs: []
	Current Language: ~~ERROR~~ NullPointerException: null
	Profiler Position: N/A (disabled)
	Vec3 Pool Size: ~~ERROR~~ NullPointerException: null
	Anisotropic Filtering: Off (1)
```

---

