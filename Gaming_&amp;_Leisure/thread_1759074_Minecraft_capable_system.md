---
title: "Minecraft capable system?"
date: 2011-05-15
forum: Gaming &amp; Leisure
---

### Post by aust77 on 2011-05-15
Hello,

I used to play Minecraft Alpha on my Inspiron 710m laptop. It's specs are in my signature. In addition, it's graphical capabilities are:
Intel 855GM with the xserver-xorg-video-intel driver installed from ppa.

My question is: Can Minecraft run on this? I have had issues with crashing on the latest Beta build, with the game citing "Only one LWGJL context may be instantiated at a time" or something along those lines (I do not have my laptop handy). I have tried both Sun and OpenJDK JVMs without success.
I have also put to use the minecraft installer SH script developed by another forums user without any success there.

I adore this game and would much enjoy getting it configured on my laptop. Any suggestions would be met with great appreciation.

Cheers,


aust77

---

### Post by aust77 on 2011-05-16
bump

---

### Post by mastablasta on 2011-05-17
another application is using LWJGL it seems. try finding out which one. and close it (if possible).
 
specs are fine.
 
Considering Unity is interfering with many tother things perhaps you could try to add a different DE to your install and then run it. Mabye it  is Unity that is interfering.

---

### Post by Dlambert on 2011-05-17
Yeah, you should have no problem. Make sure sunjava and openjdk arnt running at the same time?

---

### Post by kaldor on 2011-05-17
I find Sun Java works much better than openJDK when using NVIDIA drivers.

I have a 1.8 ghz Intel Centrino and 2 GB of RAM. Not amazingly powerful, but MC runs well enough to play.

---

### Post by mastablasta on 2011-05-18
> **kaldor said:**
> I find Sun Java works much better than openJDK when using NVIDIA drivers.

 
same goes for opensoruce ATI. In fact some java programmes won't even run with openJDK.  so i removed it and replaced it with SunJava.

---

### Post by Dlambert on 2011-05-18
+1 to sunjava being better.....not to proud of this...but runescape wont run in openjdk

---

