---
title: "Minecraft: java.lang.IllegalStateException: Only one LWJGL context ...."
date: 2010-10-11
forum: Gaming &amp; Leisure
---

### Post by Masquerade on 2010-10-11
Hey there,

I am trying to get Minecraft to run on Maverick. I have sun-java6-jre installed.

When trying to run Minecraft through the browser, or the executable .jar, I get

**java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.**

For further information, heres the log of the client:



```
      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to support@mojang.com.
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 11.10.10 20:09

Minecraft: Minecraft Alpha v1.1.2
OS: Linux (i386) version 2.6.32-22-generic
Java: 1.6.0_21, Sun Microsystems Inc.
VM: Java HotSpot(TM) Client VM (mixed mode, sharing), Sun Microsystems Inc.
LWJGL: 2.1.0
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
	at org.lwjgl.opengl.Display.create(Display.java:829)
	at org.lwjgl.opengl.Display.create(Display.java:767)
	at org.lwjgl.opengl.Display.create(Display.java:748)
	at net.minecraft.client.Minecraft.a(SourceFile:196)
	at net.minecraft.client.Minecraft.run(SourceFile:554)
	at java.lang.Thread.run(Thread.java:619)
--- END ERROR REPORT f6db50fc ----------
```

---

### Post by Sichel94 on 2010-11-07
Got exactly the same error here, I think its something with the graphics drivers, maybe you check these first...

---

### Post by Masquerade on 2010-11-07
Ye, that was exactly the issue.

---

### Post by alogghe on 2010-11-07
Maverick and Minecraft were also giving me similar crashes but reverting the Nvidia proprietary driver to the older fixed it for me.

---

### Post by Menehune on 2010-12-11
Delete the players data file on the server.
Example: <minecraft path>\world\players\<player>.dat
The player will respawn with nothing.

---

### Post by Ebonrook on 2011-03-10
If it is the graphics drivers, how do I fix it? I am still very new at this...

---

### Post by jay3 on 2011-12-26
What was the resolution to this one - how is it fixed?

---

