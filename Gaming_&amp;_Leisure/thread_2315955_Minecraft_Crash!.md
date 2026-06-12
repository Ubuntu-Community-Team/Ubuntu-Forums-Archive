---
title: "Minecraft Crash!"
date: 2016-03-03
forum: Gaming &amp; Leisure
---

### Post by jim_d. on 2016-03-03
So yeah, i'm beyond new to linux and this:

---- Minecraft Crash Report ----
// I blame Dinnerbone.


Time: 3/3/16 11:34 PM
Description: Initializing game


org.lwjgl.LWJGLException: X Error - disp: 0x7f75c869b0d0 serial: 134 error: BadValue (integer parameter out of range for operation) request_code: 155 minor_code: 24
	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:320)
	at org.lwjgl.opengl.LinuxContextImplementation.nCreate(Native Method)
	at org.lwjgl.opengl.LinuxContextImplementation.create(LinuxContextImplementation.java:51)
	at org.lwjgl.opengl.ContextGL.<init>(ContextGL.java:132)
	at org.lwjgl.opengl.Display.create(Display.java:850)
	at org.lwjgl.opengl.Display.create(Display.java:757)
	at org.lwjgl.opengl.Display.create(Display.java:739)
	at bcf.ap(SourceFile:594)
	at bcf.an(SourceFile:430)
	at bcf.a(SourceFile:377)
	at net.minecraft.client.main.Main.main(SourceFile:124)




A detailed walkthrough of the error, its code path and all known details is as follows:
---------------------------------------------------------------------------------------


-- Head --
Stacktrace:
	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:320)
	at org.lwjgl.opengl.LinuxContextImplementation.nCreate(Native Method)
	at org.lwjgl.opengl.LinuxContextImplementation.create(LinuxContextImplementation.java:51)
	at org.lwjgl.opengl.ContextGL.<init>(ContextGL.java:132)
	at org.lwjgl.opengl.Display.create(Display.java:850)
	at org.lwjgl.opengl.Display.create(Display.java:757)
	at org.lwjgl.opengl.Display.create(Display.java:739)
	at bcf.ap(SourceFile:594)
	at bcf.an(SourceFile:430)


-- Initialization --
Details:
Stacktrace:
	at bcf.a(SourceFile:377)
	at net.minecraft.client.main.Main.main(SourceFile:124)


-- System Details --
Details:
	Minecraft Version: 1.9
	Operating System: Linux (amd64) version 4.2.0-27-generic
	Java Version: 1.7.0_95, Oracle Corporation
	Java VM Version: OpenJDK 64-Bit Server VM (mixed mode), Oracle Corporation
	Memory: 66910120 bytes (63 MB) / 167219200 bytes (159 MB) up to 1060372480 bytes (1011 MB)
	JVM Flags: 5 total; -Xmx1G -XX:+UseConcMarkSweepGC -XX:+CMSIncrementalMode -XX:-UseAdaptiveSizePolicy -Xmn128M
	IntCache: cache: 0, tcache: 0, allocated: 0, tallocated: 0
	Launched Version: 1.9
	LWJGL: 2.9.4
	OpenGL: ~~ERROR~~ RuntimeException: No OpenGL context found in the current thread.
	GL Caps: 
	Using VBOs: No
	Is Modded: Probably not. Jar signature remains and client brand is untouched.
	Type: Client (map_client.txt)
	Resource Packs: 
	Current Language: ~~ERROR~~ NullPointerException: null
	Profiler Position: N/A (disabled)
	CPU: <unknown>

---

