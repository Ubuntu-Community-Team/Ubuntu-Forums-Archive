---
title: "America's Army problem"
date: 2005-03-25
forum: Gaming &amp; Leisure
---

### Post by macmasterxiv on 2005-03-25
When I try to run America's Army, the splash screen comes up, but then it bails. I'm running hoary with the fglrx drivers. For the record, UT2004 (demo) runs fine. ```
jm@ubuntu:~$ armyops
open /dev/[sound/]dsp: Device or resource busy
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
GL_EXT_bgra not supported - bailing out.

History:

Exiting due to error
```

Update: Also for the record, ET, Quake3, and UT all want to use Mesa rendering instead of fglrx. I'm starting to think that all these programs (except UT2004) are reading a Mesa libGL.so.1 instead of the proper hardware accelerated one.
```
jm@ubuntu:~$ et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/jm/.etwolf/etmain
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

---

### Post by Krpano on 2005-03-26
I have the same problem....
arghhh

---

### Post by macmasterxiv on 2005-03-26
I have found the problematic file. It appears that the 64 bit version of libGL.so.1.2 located in /usr/X11R6/lib is fine, that's why UT2004 works, however the 32 bit version of that, located in /usr/X11R6/lib32 is either a mesa library or is running mesa for some strange reason. Is this a bug in the package?

---

### Post by macmasterxiv on 2005-03-27
[QUOTE=macmasterxiv]I have found the problematic file. It appears that the 64 bit version of libGL.so.1.2 located in /usr/X11R6/lib is fine, that's why UT2004 works, however the 32 bit version of that, located in /usr/X11R6/lib32 is either a mesa library or is running mesa for some strange reason. Is this a bug in the package?[/QUOTE]
 I SOLVED IT! all you need to do is use "export LIBGL_DRIVERS_DIR=/usr/X11R6/lib32/modules/dri" and everything should then work

---

### Post by draxula on 2005-04-06
Hi,

I have similiar problem, but sound related ](*,)  (no sound).

I get the following:

stephan@stephan-x64:~$ armyops
open /dev/[sound/]dsp: Device or resource busy

Any ideas?

TIA
Stephan

---

### Post by draxula on 2005-04-06
hi again,

just being stupid :-\"

did not read next thread.

btw: do you have to kill esd every time?

TIA
Stephan

---

### Post by macmasterxiv on 2005-04-06
[QUOTE=draxula]hi again,

just being stupid :-\"

did not read next thread.

btw: do you have to kill esd every time?

TIA
Stephan[/QUOTE]
 once you kill esd, you don't have to do it again until you logout, then it is reset

---

### Post by OpenWebTech on 2005-04-10
[QUOTE=macmasterxiv]I SOLVED IT! all you need to do is use "export LIBGL_DRIVERS_DIR=/usr/X11R6/lib32/modules/dri" and everything should then work[/QUOTE]

Maybe I'm missing something here, /usr/X11R6/lib32 does not exist on my system. I do however have /usr/X11R6/lib  which has /modules/dri.

By using "export LIBGL_DRIVERS_DIR=/usr/X11R6/[COLOR=Red]lib[/COLOR]/modules/dri" I was able to get through the first 2 training exercises but then crashed with the following error...

```
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Signal: SIGSEGV [segmentation fault]
Aborting.

Crash information will be saved to your logfile.

``` 

Is there something else I should have done here?

Tom

---

### Post by macmasterxiv on 2005-04-10
[QUOTE=OpenWebTech]Maybe I'm missing something here, /usr/X11R6/lib32 does not exist on my system. I do however have /usr/X11R6/lib  which has /modules/dri.

By using "export LIBGL_DRIVERS_DIR=/usr/X11R6/[COLOR=Red]lib[/COLOR]/modules/dri" I was able to get through the first 2 training exercises but then crashed with the following error...

```
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Signal: SIGSEGV [segmentation fault]
Aborting.

Crash information will be saved to your logfile.

``` 

Is there something else I should have done here?

Tom[/QUOTE]

You have a completely different problem. This problem I was having pertains to amd64 systems. That's why you don't have a lib32 folder.

As for your problem, if you could post your logfile, that would be helpful.

---

