---
title: "Minecraft error on startup"
date: 2013-01-13
forum: Gaming &amp; Leisure
---

### Post by Uniplex on 2013-01-13
Hiya!
I just got Ubuntu, so when I installed Minecraft at first it worked fine; but when I tried again a bit later, this error was thrown up on startup: (I started it from the terminal)


27 achievements
210 recipes
Setting user: Uniplex, af56d42a7267f04f80025b12778f0bf6ae01b3f8
LWJGL Version: 2.4.2
Xlib:  extension "GLX" missing on display ":0".
org.lwjgl.LWJGLException: Could not init GLX
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
	at org.lwjgl.opengl.Display.create(Display.java:854)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at net.minecraft.client.Minecraft.a(SourceFile:223)
	at asq.a(SourceFile:56)
	at net.minecraft.client.Minecraft.run(SourceFile:515)
	at java.lang.Thread.run(Thread.java:679)
Xlib:  extension "GLX" missing on display ":0".
org.lwjgl.LWJGLException: Could not init GLX
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:684)
	at org.lwjgl.opengl.Display.create(Display.java:854)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:232)
	at asq.a(SourceFile:56)
	at net.minecraft.client.Minecraft.run(SourceFile:515)
	at java.lang.Thread.run(Thread.java:679)

If someone could help me, that'd be great :)

---

### Post by Uniplex on 2013-01-13
Also, I used the command
```
java -jar minecraft.jar
```
to start it.

---

### Post by entw on 2013-01-13
First update your lwjgl. As you can see [here]("http://lwjgl.org/download.php") actual version is 2.8.5.

---

### Post by entw on 2013-01-13
```
~/.minecraft/bin
./natives/
    libjinput-linux.so
    liblwjgl.so
    libopenal.so
jinput.jar
lwjgl.jar
lwjgl_util.jar
```These are the files you need to replace. Also tell us your java version (you can use the following command: java -version).

---

### Post by Uniplex on 2013-01-13
Replaced all the files, but I'm still getting an error. This time I copy-pasted it from the crash-reports text file:
```
---- Minecraft Crash Report ----
// Hey, that tickles! Hehehe!

Time: 1/13/13 2:49 PM
Description: Failed to start game

org.lwjgl.LWJGLException: Could not init GLX
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
	at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:61)
	at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:788)
	at org.lwjgl.opengl.DrawableGL.setPixelFormat(DrawableGL.java:61)
	at org.lwjgl.opengl.Display.create(Display.java:843)
	at org.lwjgl.opengl.Display.create(Display.java:754)
	at org.lwjgl.opengl.Display.create(Display.java:736)
	at net.minecraft.client.Minecraft.a(SourceFile:232)
	at asq.a(SourceFile:56)
	at net.minecraft.client.Minecraft.run(SourceFile:515)
	at java.lang.Thread.run(Thread.java:679)


A detailed walkthrough of the error, its code path and all known details is as follows:
---------------------------------------------------------------------------------------

-- System Details --
Details:
	Minecraft Version: 1.4.7
	Operating System: Linux (amd64) version 3.2.0-35-generic
	Java Version: 1.6.0_24, Sun Microsystems Inc.
	Java VM Version: OpenJDK 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
	Memory: 91006448 bytes (86 MB) / 123797504 bytes (118 MB) up to 1838088192 bytes (1752 MB)
	JVM Flags: 0 total; 
	AABB Pool Size: 0 (0 bytes; 0 MB) allocated, 0 (0 bytes; 0 MB) used
	Suspicious classes: No suspicious classes found.
	IntCache: cache: 0, tcache: 0, allocated: 0, tallocated: 0
	LWJGL: 2.8.4
	OpenGL: ~~ERROR~~ NullPointerException: null
	Is Modded: Probably not. Jar signature remains and client brand is untouched.
	Type: Client (map_client.txt)
	Texture Pack: Default
	Profiler Position: N/A (disabled)
	Vec3 Pool Size: ~~ERROR~~ NullPointerException: null
```

---

### Post by Uniplex on 2013-01-13
Also, I'm running OpenJDK 6.

---

### Post by holastickboy on 2013-01-13
> **Uniplex said:**
> Also, I'm running OpenJDK 6.

First things first, please install Oracle Java, particularly Java 7 for Minecraft and other Java games.

I have made a simple tutorial for Ubuntu 12.04, but this also works with 12.10 (which is what I am running now).

[http://youtu.be/sHKZMy1taPg](http://youtu.be/sHKZMy1taPg)

---

### Post by scarabcoder on 2013-01-13
Have you tried re-installing it? To do that, go to your home folder, and do Ctrl+H. Look for the folder called ".minecraft". Just delete it, then run the Minecraft.jar file that you downloaded from minecraft.net.

---

### Post by entw on 2013-01-14
> **Uniplex said:**
> Replaced all the files, but I'm still getting an errorOh, you need also x64 libraries, which are present in lwjgl zip-package. Forgot to mention that after replacing of lwjgl files you must restart your X-session.

---

### Post by crdbaby on 2013-04-02
[COLOR=#000000]I was using Open JDK 6 and getting the same error as the OP. I've been trying all day to get minecraft working for my son, but after entering the login and password, it would crash and give me a crash report that cited lwgjl as the problem. I installed Oracle 7 as recommended above, and now all I get after login is a black screen. I'm running ubuntu 12.04, and I'm out of ideas. Please help![/COLOR]

---

### Post by Ender Shadow on 2013-04-02
I think that the OP's problem has something to do with OpenGL, as indicated by this:

```

OpenGL: ~~ERROR~~ NullPointerException: null
```

EDIT: Although it doesn't seem like the OP has been around in a while...

---

