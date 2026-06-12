---
title: "Having some Issuse with MineCraft but the issues are from Ubuntu i Think"
date: 2011-09-26
forum: Gaming &amp; Leisure
---

### Post by miahbesmokin420 on 2011-09-26
So basically i have asked for help on the MineCraft forums and other places but everyone seems to think that its a issue with my OS possibly some drivers or something like that idk

So basically whats going on is this
MineCraft 1.7.3 worked with no problems
MineCraft 1.8 wont stop crashing

Apparently they did some changes on some of the lighting which uses OpenGLX i think
ya so what i have tried is the following:
Current Version of Sun Java 6 = Random Crash
Current Version of Sun Java 7 = Random Crash
Current Version of OpenJRE = Random Crash
Current and Nightly Builds of LWJGL = Random Crash
Ubuntu 10.04 and 11.04 = Random Crash
Removed the novudo?? i think its called drivers for nvidia and installed the official nvidia drivers from the nvidia website and still = Random Crash

Now i might have tried more things but i dont remember but im willing to try anything to get this working with out crashing. Attached is the Error that is Received After the Crash.
Also Note that the error is the same almost every time.
Any Help would be Great full and much appreciated and thank in advance :)

```

java.lang.NullPointerException
    at kj.b(SourceFile:483)
    at wd.a_(EntityLiving.java:605)
    at wd.p(EntityLiving.java:763)
    at tb.p(SourceFile:26)
    at wd.w_(EntityLiving.java:255)
    at tb.w_(SourceFile:30)
    at sn.w_(SourceFile:65)
    at rv.a(SourceFile:1268)
    at rv.f(SourceFile:1244)
    at rv.l(SourceFile:1178)
    at net.minecraft.client.Minecraft.k(SourceFile:1384)
    at net.minecraft.client.Minecraft.run(SourceFile:666)
    at java.lang.Thread.run(Unknown Source)
Stopping!

SoundSystem shutting down...
    Author: Paul Lamb, www.paulscode.com

Exception in thread "Minecraft main thread" org.lwjgl.LWJGLException: X Error - disp: 0xa036090 serial: 34462 error: BadWindow (invalid Window parameter) request_code: 2 minor_code: 0
    at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:277)
    at org.lwjgl.opengl.LinuxKeyboard.nSetDetectableKeyRepeat(Native Method)
    at org.lwjgl.opengl.LinuxKeyboard.setDetectableKeyRepeat(LinuxKeyboard.java:152)
    at org.lwjgl.opengl.LinuxKeyboard.destroy(LinuxKeyboard.java:163)
    at org.lwjgl.opengl.LinuxDisplay.destroyKeyboard(LinuxDisplay.java:1061)
    at org.lwjgl.input.Keyboard.destroy(Keyboard.java:349)
    at net.minecraft.client.Minecraft.d(SourceFile:506)
    at net.minecraft.client.Minecraft.run(SourceFile:750)
    at java.lang.Thread.run(Unknown Source)

```Also note that i Registered back in 2009 and this is my first post and thats because i always research my problems very well before asking for help
but this is a problem that is making me go crazy and loose my mind, because this is one that i can not fix or find a fix for.

---

