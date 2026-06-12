---
title: "Wolfenstein Enemy Territory video problem"
date: 2005-08-02
forum: Gaming &amp; Leisure
---

### Post by Navyblue on 2005-08-02
I have installed Enemy Territories and I could not start the game, I get this message after typing "et" at the console.

```

Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

```

I am able to start the game by adding "+set r_allowSoftwareGL 1" as suggested but the game is crawling and definitely not playable. I have installed the fglrx driver. How do I enable the hardware openGL?

Btw, my glxgears score is above 1000 FPS.

---

### Post by Mishura on 2005-08-02
The reason why it won't work is because you are using the MesaGL libraries instead of Hardware accelerated GL drivers from ATi or Nvidia.

You will need to install the correct drivers for your card.  As far as I know, Mesa will not work with the Quake3-based games like ET.

---

### Post by Navyblue on 2005-08-02
I have installed the fglrx driver for my ATI 9550. And from the glxgears score it seems to be working. My OpenGL screen saver is much faster now compared to before I installed the fglrx.

---

### Post by Navyblue on 2005-08-02
Does this game only work with xfree86 drivers?

---

### Post by strikeforce on 2005-08-02
xfree86 and xorg are similar in nature and both are based off of the same thing if you see xorg then equivalate that to xfree86

---

### Post by Navyblue on 2005-08-02
[QUOTE=strikeforce]xfree86 and xorg are similar in nature and both are based off of the same thing if you see xorg then equivalate that to xfree86[/QUOTE]
 So what do I need to do in order to stop it from looking for xfree86 driver and take in my xorg driver?

Is there any command that allows me to force it to do so like the command for software opengl rendering?

---

### Post by Navyblue on 2005-08-02
Does it has anything to do with the fact that I am running 64 bit cersion of Ubuntu?

---

### Post by Yagisan on 2005-08-02
I also run amd64 ubuntu. ET needs 32bit opengl drivers. Could you check in /usr/lib32 to see if fglrx installed 32bit opengl drivers. I have a nvidia card, and the ubuntu nvidia package automaticially installed 32bit opengl drivers in /usr/lib32 for me.

---

### Post by Navyblue on 2005-08-02
Nope, nothing in /usr/lib32. But there is a link in /usr/lib and /usr/lib64.

What can I do?

---

### Post by Yagisan on 2005-08-02
apt-get install ia32-libs might help

---

### Post by baRRacuda on 2005-08-02
[QUOTE=Navyblue]Nope, nothing in /usr/lib32. But there is a link in /usr/lib and /usr/lib64.

What can I do?[/QUOTE]
 there's something about that here : [http://ubuntuforums.org/showthread.php?t=20268](http://ubuntuforums.org/showthread.php?t=20268)
(it's for warthy but you can try on hoary :) )

---

### Post by Navyblue on 2005-08-02
[QUOTE=Yagisan]apt-get install ia32-libs might help[/QUOTE]
 I have the latest version installed already.

Btw, just installed America's Army, when I launch it, it shows a splash screen and restarted X.

I wanted to install wine and it doesn't work too.

So should I be getting the 32 bit version Ubuntu instead in order to play games?

---

### Post by Navyblue on 2005-08-02
[QUOTE=baRRacuda]there's something about that here : [http://ubuntuforums.org/showthread.php?t=20268](http://ubuntuforums.org/showthread.php?t=20268)
(it's for warthy but you can try on hoary :) )[/QUOTE]

Thanks, that sounds easy, hopefully I can do it.

---

### Post by Navyblue on 2005-08-03
[QUOTE=baRRacuda]there's something about that here : [http://ubuntuforums.org/showthread.php?t=20268](http://ubuntuforums.org/showthread.php?t=20268)
(it's for warthy but you can try on hoary :) )[/QUOTE]

The method WORKS!!!

Thanks so much! :)

---

### Post by baRRacuda on 2005-08-03
[QUOTE=Navyblue]The method WORKS!!!

Thanks so much! :)[/QUOTE]
 You're welcome...

But you would have found the solution faster if you had searched the forum.. [-X :grin:

---

