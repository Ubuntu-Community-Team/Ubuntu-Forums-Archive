---
title: "Help required with minecraft"
date: 2011-09-25
forum: Gaming &amp; Leisure
---

### Post by mcSavagekilla on 2011-09-25
I need some help running my Minecraft. when i open the Minecraft .jar and run it with sun java or open JDK i get this error message:


--- BEGIN ERROR REPORT a1dce528 --------
Generated 25/09/11 6:24 PM

Minecraft: Minecraft Beta 1.8.1
OS: Linux (i386) version 2.6.38-11-generic
Java: 1.6.0_26, Sun Microsystems Inc.
VM: Java HotSpot(TM) Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
	at org.lwjgl.opengl.Display.create(Display.java:846)
	at org.lwjgl.opengl.Display.create(Display.java:784)
	at org.lwjgl.opengl.Display.create(Display.java:765)
	at net.minecraft.client.Minecraft.a(SourceFile:233)
	at net.minecraft.client.Minecraft.run(SourceFile:629)
	at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT 76da1f94 ----------

how the brown does i fix?
cause i am banging my head on the keyboard literally 
](*,)](*,)](*,)](*,)

---

### Post by markg48 on 2011-09-25
just posted a fix here [http://ubuntuforums.org/showthread.php?t=1849846](http://ubuntuforums.org/showthread.php?t=1849846)

if you have ati graphics it might help

---

### Post by mcSavagekilla on 2011-09-25
it didnt work it just said it coulnt locate the minecraft launcher
*sniff* WHYYYYYYYYYYYYYYY cant it just work? whyyyyyyyyyyyyy!!!!!??

---

### Post by markg48 on 2011-09-26
beacause you didnt do it properly open terminal env LIBGL_ALWAYS_INDIRECT=1 java -Xmx1024M -Xms512M -cp /home/yoursname/Desktop/Minecraft.jar net.minecraft.LauncherFrame

replace yourname with your user name if your mien craft launcher isnt on the desktop it wont work and it must b named minecraft.jar

---

