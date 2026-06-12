---
title: "Wolfenstein Enemy Territory"
date: 2006-06-23
forum: Gaming &amp; Leisure
---

### Post by lwr on 2006-06-23
Hi,

I'm attempting to install Wolfenstein: Enemy Territory. I'm pretty new to linux, so I just kind of guessed what to do. I found a post that said to do this:
 sh ./et-linux-2.55.x86.run
and it all seemed to work fine, but when I try to run it, all it does is make the screen go black briefly then bring my desktop back in an ultra-low resolution. Any ideas what I need to do?

Thanks

---

### Post by x64Jimbo on 2006-06-23
Just out of curiosity, do you have the 3d drivers installed for your system?

---

### Post by lwr on 2006-06-23
Probably not. How do I find out what I need and where do I get them from?

---

### Post by nitricacid on 2006-06-23
lwr, What kind of graphic card do you have?

---

### Post by lwr on 2006-06-29
I'm not sure. Can I found out in device manager?

---

### Post by Brucevdk on 2006-06-30
[QUOTE=lwr]Hi,

I'm attempting to install Wolfenstein: Enemy Territory. I'm pretty new to linux, so I just kind of guessed what to do. I found a post that said to do this:
 sh ./et-linux-2.55.x86.run
and it all seemed to work fine, but when I try to run it, all it does is make the screen go black briefly then bring my desktop back in an ultra-low resolution. Any ideas what I need to do?

Thanks[/QUOTE]

Hello lwr, 

To help you some more information would be appreciated. First thing you should do is open up a terminal (Applications->Accessoires->Terminal) and execute the command "et" (without quotes). If this doesn't work, change to the directory where you installed Enemy Territory (likely /home/<your username>/enemy-territory) using "cd" and type ./et

However if it does succeed, proceed to paste the text in the terminal in a reply between ```
 tags. Also paste the output of the following commands:

[CODE]
glxinfo | egrep '(OpenGL (vendor|renderer|version)|rendering)'
lspci | grep 'Display'

```

After that you should look at a file in /etc/X11/ called xorg.conf, copy this file to your desktop, zip it and attach it to your reply.

---

### Post by lwr on 2006-06-30
Hi
Running et gave me this:
```

ET 2.55 linux-i386 May 27 2003
----- FS_Startup -----
Current search path:
/home/luke/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (4 files)
/usr/local/games/enemy-territory/etmain

----------------------
3729 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
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
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
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

The  first line of your code gave me this:
```

direct rendering: No
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

The second line didn't produce anything.

Thanks for your help

---

### Post by lwr on 2006-07-17
It's all sorted now. I realised I needed to use the nvidia legacy drivers. Sadly, I don't think my graphics card is up to it, as things are quiute slow. Oh well.
Thanks to everyone for all their help and advice.

---

