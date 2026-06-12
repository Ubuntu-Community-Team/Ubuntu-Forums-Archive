---
title: "Minecraft will not run."
date: 2011-02-13
forum: Gaming &amp; Leisure
---

### Post by GazerDwarf on 2011-02-13
I am an Ubuntu noob so I can't get much more complected than copying and pasting in terminal, I will try though. OK the problem is when I run minecraft by any means I've found (right click and open with sun java 6, Terminal 'java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame' and several simalar ones) I can always get to the log on screen but once I log it the loading bars do their thing and the screen goes black for a while. Then I get this message from the window:
Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to [EMAIL="support@mojang.com"]support@mojang.com[/EMAIL].
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 13/02/11 11:57 PM

Minecraft: Minecraft Beta 1.2_02
OS: Linux (amd64) version 2.6.35-25-generic
Java: 1.6.0_20, Sun Microsystems Inc.
VM: OpenJDK 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
    at org.lwjgl.opengl.Display.create(Display.java:846)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(SourceFile:243)
    at net.minecraft.client.Minecraft.run(SourceFile:606)
    at java.lang.Thread.run(Thread.java:636)
--- END ERROR REPORT c654b941 ----------
I just can't get it to work. :confused:

I think it is also relevant that I am running Ubuntu 10.10 64 bit and have had trouble with the display driver (I think). When I installed the Ubuntu updates and reset the screen would go black but when I used the fail safe driver it was fine so I removed the new one. The video card is a Radeon HD 6970.

Any ideas?

---

### Post by karth on 2011-02-13
Looks like you're having issues with OpenGL, which relies on the 3D capabilities of your card and driver.

What is the output of :
```
glxinfo | grep rendering
```

If it says "Direct rendering: No", the you might have issue with everything related to 3D acceleration.

Anyway, I think you should try to get the ATI driver working. How about a try with the System > Administration > Drivers GUI to see how it goes? Radeon HD 6970 seems to be a quite new card out in the market, so it should be well supported by ATI... unless the drivers have not been properly updated since it went out.

---

