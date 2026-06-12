---
title: "ET Problem."
date: 2006-01-27
forum: Gaming &amp; Leisure
---

### Post by Sirin on 2006-01-27
Hello, I have a problem with my ET startup.

I successfully installed everything, but when I go to run ET all it does is fade to blacK, just to unexpectedly quit. 

If you need to know, my video card is an Intel 82865G IGD.

Any ideas?

---

### Post by Sirin on 2006-01-27
Grabbed the command line log. This is what it says:

```
root@cpe-65-26-156-150:/home/[*****]# et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/root/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
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

Anybody know how to fix this problem?

---

### Post by Madpilot on 2006-01-27
I'm pretty sure you don't have 3d acceleration running - that's what the "You are using software Mesa (no hardware acceleration)" line partway thru that file means.

If you've got an ATI graphics card: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

... if NVidia: [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

Also, ET has it's own Ubuntu wiki page: [https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)

It does run very nicely on Breezy, once you get your 3d card set up!

---

### Post by Sirin on 2006-01-27
[QUOTE=Madpilot]I'm pretty sure you don't have 3d acceleration running - that's what the "You are using software Mesa (no hardware acceleration)" line partway thru that file means.

If you've got an ATI graphics card: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

... if NVidia: [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

Also, ET has it's own Ubuntu wiki page: [https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)

It does run very nicely on Breezy, once you get your 3d card set up![/QUOTE]

Actually, I have an Intel Integrated card. It ran very nice on Windows, but somehow, it just doesn't work with Linux.

---

### Post by PLAY3ER on 2006-01-28
i know this is not the topic but no one anwersed my post, how can i set up ET and TS to use the sound at the same time?


thanks, [email]ryan.macintosh@gmail.com[/email] (MSN+Emai)

---

### Post by Sirin on 2006-02-08
Anybody Find anything, yet?

---

### Post by Perfect Storm on 2006-02-08
[http://ubuntuforums.org/showthread.php?t=27029&highlight=82865G](http://ubuntuforums.org/showthread.php?t=27029&highlight=82865G)
might help just read the whole thread.

---

### Post by Sirin on 2006-03-03
[QUOTE=Artificial Intelligence][http://ubuntuforums.org/showthread.php?t=27029&highlight=82865G](http://ubuntuforums.org/showthread.php?t=27029&highlight=82865G)
might help just read the whole thread.[/QUOTE]

Nope. Didn't work. :cry: 

To be more descriptive, Enemy Territory will not start with Breezy. I get a black screen that I can move around and see a larger desktop underneath. Not sure whats going on. ET works fine in Fedora Core 1, which sports XFree86.

---

### Post by Sirin on 2006-03-16
Anybody? [IMG]http://67.18.37.14/86/93/emo/cry.gif[/IMG]

---

### Post by Perfect Storm on 2006-03-16
and ubuntu shows the gears when typing glxgears in the terminal?

---

### Post by Sirin on 2006-03-16
[QUOTE=Artificial Intelligence]and ubuntu shows the gears when typing glxgears in the terminal?[/QUOTE]

Very fluidly.

---

