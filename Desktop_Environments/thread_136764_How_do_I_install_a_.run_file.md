---
title: "How do I install a .run file?"
date: 2006-02-26
forum: Desktop Environments
---

### Post by mztriz on 2006-02-26
I am trying to install Enemy Territory but I'm not quite sure how. Its file extention is .run.

Thanks,
Ava :)

---

### Post by vbmaster on 2006-02-26
$sudo sh nameoffile.run

;)

---

### Post by mztriz on 2006-02-26
Thanks but it didn't quite work
```
sudo: sh/home/mztriz/Desktop/et-linux-2.60-update.x86.run: command not found

```


EDIT: Nevermind I figured it out -_-
Thank you!

---

### Post by mztriz on 2006-02-26
What's default.cfg?
```
Sys_Error: Couldn't load default.cfg - I am missing essential files - verify you r installation?
```

---

### Post by vbmaster on 2006-02-26
[QUOTE=mztriz]What's default.cfg?
```
Sys_Error: Couldn't load default.cfg - I am missing essential files - verify you r installation?
```[/QUOTE]

Ops... i didn't release that was Enemy Territory that you're trying to install, i've sucessfuly install that great game btw... :P

Remeber that first you'll need you graphicboard drivers installed, folow this: [https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

To enemy folow this: [https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)

Stay cool ;)

**EDIT**: The command actually was '$ sudo sh ./namoeoffile.run' ;)

---

### Post by mztriz on 2006-02-26
```
 sudo et
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/adam/.etwolf/etmain
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
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get a visual
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem



```

---

### Post by ljs662 on 2007-07-02
When you download something in linux it will not automatically make it executable.
try this...


navigate to the directory that the file is in,


chmod +x nameoffile.run


./nameoffile.run

---

### Post by Likenota on 2007-07-16
yea too bad none of that stuff you guys posted even works.. can i please get some help here..

---

### Post by delusion77 on 2007-11-15
> **ljs662 said:**
> When you download something in linux it will not automatically make it executable.
try this...


navigate to the directory that the file is in,


chmod +x nameoffile.run


./nameoffile.run

this is the way i now do it. :P TYVM

---

### Post by zmathe on 2008-06-29
hi! 

Follow the procedure below to install software packaged in a .run file:

   1.

      Find the .run file in the File Browser
   2.

      Right-click the file and select Properties
   3.

      Under the Permissions tab, make sure that Allow executing file as program is ticked and press Close
   4. Double-click the .run file to open it. A dialog box should appear
   5.

      Press Run in Terminal to run the installer
   6.

      A Terminal window will open. Follow any instructions on-screen to install the program

Have Fun! :guitar:

---

