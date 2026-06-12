---
title: "Wolfenstein Enemy Territory 2.60 Installer"
date: 2007-08-31
forum: Gaming &amp; Leisure
---

### Post by AzraelSlain on 2007-08-31
ok after alot of looking around and getting the "right" installer, i got the 2.60 installer, made the .run file,  then 

sudo sh et-linux-2.60.x86.run

then i get this error
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install..............................................................................................................................................................................................................................................................................................................................
./setup.sh: 278: /home/azrael/.setup7641: not found
./setup.sh: 289: /home/azrael/.setup7641: not found


any ideas?

---

### Post by asipi on 2007-09-02
something unexpected...
do you have enough freespace on the drive where you started the installer?
check th 2 lines mentioned in that setup.sh script but guess it is only temporary and autoremoved when installer fails.

anyway I installed ET several times without any problem so it should work. At a last chance try to download the installer from a different location there are plenty on the net.

---

### Post by AzraelSlain on 2007-09-02
Have a 200 gig SATA drive, outside of the operating system itself, nothing else on it. How do i check the script? I'm still very new to linux, thankfully i learn more each time around. So whats the command line for what i got to put in the terminal? thanks for help by the way.

---

### Post by toolfreakuna on 2007-09-02
I am having the same problem with ET. Could this issue have anything to do with 64-bit Ubuntu? I have almost 500 GB free on the disk I'm using.

---

### Post by SOULRiDER on 2007-09-02
toolfreakuna I would try to free some more space just in case.

---

### Post by DJ_Max on 2007-09-02
I doubt you have a space issue. To check
```

df -h

```

What are your specs? A search yields
[http://ubuntuforums.org/showthread.php?t=416871](http://ubuntuforums.org/showthread.php?t=416871)

---

### Post by DoktorSeven on 2007-09-02
Another thing to try: by default **sh** is linked to "dash" which isn't fully compatible with the bash interpreter.  Try **sudo bash et-linux-2.60.x86.run**

If that doesn't work, the download might be corrupted, try getting it again.

---

### Post by AzraelSlain on 2007-09-04
ok, got it installed, but now when i run it, i get the following

ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/azrael/.etwolf/etmain
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


Ok, i got a Nvidia GS 7300 Card with 256M.

---

### Post by stinger30au on 2007-09-04
this may help
[http://ubuntuforums.org/showthread.php?t=542348](http://ubuntuforums.org/showthread.php?t=542348)

---

### Post by AzraelSlain on 2007-09-05
yay i got it, thanks guys

---

### Post by rcdegges on 2007-09-05
If you want, I just wrote my own installer for the game which makes your life a little easier (in my opinion). Check ou this thread:

[http://ubuntuforums.org/showthread.php?t=542348](http://ubuntuforums.org/showthread.php?t=542348)

or here:

[http://projectb14ck.org/scripts/](http://projectb14ck.org/scripts/)

-Randall

---

