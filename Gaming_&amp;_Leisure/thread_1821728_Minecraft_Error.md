---
title: "Minecraft Error"
date: 2011-08-09
forum: Gaming &amp; Leisure
---

### Post by Schweinessener on 2011-08-09
This seems as though its been asked everywhere but i havent been able to find a solution. whenever i run minecraft, after logging in it gives a blank screen and then displays this:



      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.

If you wish to report this, please copy this entire text and email it to [email]support@mojang.com[/email].
Please include a description of what you did when the error occured.



--- BEGIN ERROR REPORT a1dce528 --------
Generated 8/9/11 1:32 PM

Minecraft: Minecraft Beta 1.7.3
OS: Linux (amd64) version 2.6.38-10-generic
Java: 1.6.0_26, Sun Microsystems Inc.
VM: Java HotSpot(TM) 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

java.lang.IllegalStateException: Only one LWJGL context may be instantiated at any one time.
    at org.lwjgl.opengl.Display.create(Display.java:846)
    at org.lwjgl.opengl.Display.create(Display.java:784)
    at org.lwjgl.opengl.Display.create(Display.java:765)
    at net.minecraft.client.Minecraft.a(SourceFile:294)
    at net.minecraft.client.Minecraft.run(SourceFile:716)
    at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT 34844d4f ----------


I uninstalled the open java runtime thing as many 'fixes' have instructed me to do so. it runs with the sun java runtime, and i have all of these downloaded from the canonical partners thing. im not sure how to 'If you run into out of memory errors, try launching it with java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
Also, please make sure you're running the Sun JVM...' but i dont think itd fix the problem. how can i get minecraft working?

---

### Post by kunal00731 on 2011-08-29
Hi [Schweinessener]("http://ubuntuforums.org/member.php?u=1393101"),
I am very sorry to say that, this is an inherent problem in this game and the bug fix for this still has not happened. So we need to wait until something comes up. ---> a fellow gamer.
If  you find  out any fix  , then kindly let me know.

---

### Post by Schweinessener on 2011-08-29
aw poo :( i dunno tho, i mean it doesnt recognize my graphics card, i think that might be it.

---

### Post by donkyhotay on 2011-08-30
It might be a video card issue. The error doesn't have anything specific with ubuntu though and is from minecraft itself which is why we don't know the answer to it. Minecraft forum would be more likely to help with this.

---

