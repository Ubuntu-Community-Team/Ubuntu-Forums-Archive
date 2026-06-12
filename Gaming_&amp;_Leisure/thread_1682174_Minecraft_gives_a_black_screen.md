---
title: "Minecraft gives a black screen"
date: 2011-02-05
forum: Gaming &amp; Leisure
---

### Post by theyain on 2011-02-05
I've been playing Minecraft for a couple weeks now (probably two months), but yesterday after logging in I'm presented with a black screen instead of the 'Mojang Specifications' logo.

Terminal shows this set errors:

```


zombies-e@brains:~$ java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
Username is 'theyainthefox'
28
Setting user: theyainthefox, -119817934262561913
Exception in thread "Minecraft main thread" java.lang.ExceptionInInitializerError
	at net.minecraft.client.Minecraft.a(SourceFile:195)
	at net.minecraft.client.Minecraft.run(SourceFile:606)
	at java.lang.Thread.run(Thread.java:636)
Caused by: java.lang.ArrayIndexOutOfBoundsException: 0
	at org.lwjgl.opengl.XRandR$Screen.<init>(XRandR.java:234)
	at org.lwjgl.opengl.XRandR$Screen.<init>(XRandR.java:196)
	at org.lwjgl.opengl.XRandR.populate(XRandR.java:87)
	at org.lwjgl.opengl.XRandR.access$100(XRandR.java:52)
	at org.lwjgl.opengl.XRandR$1.run(XRandR.java:110)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.lwjgl.opengl.XRandR.getConfiguration(XRandR.java:108)
	at org.lwjgl.opengl.LinuxDisplay.init(LinuxDisplay.java:618)
	at org.lwjgl.opengl.Display.<clinit>(Display.java:135)
	... 3 more

```

I know from messing around that the minecraft jar file is not at fault, neither is anything in the /.minecraft directory.  I'm using sun jvm.  It less then three days ago...

I'm thinking that this might be related to my intel graphics driver updating a couple days ago.  Anyone have any suggestions?

---

### Post by theyain on 2011-02-05
Well, I decided to boot an older, kernel and that seems to fix it.  It seems the latest kernel breaks java in some way.

---

### Post by EGadZooks on 2011-09-21
can i get a description of which kernel you were using and which one you are using now?

also, do you have any experience with the newest 1.8 release?

---

