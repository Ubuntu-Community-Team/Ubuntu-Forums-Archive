---
title: "Enemy Territory Sluggish"
date: 2006-09-08
forum: Gaming &amp; Leisure
---

### Post by Inhumane on 2006-09-08
Just installed ET, but the movement ingame is really laggy, the FPS is fine but it takes about 3 seconds to respond to mouse movement and keyboard pressing.. What's wrong?

---

### Post by Izuil on 2006-09-08
I'm pretty much a noob at Linux and all this but I would guess you're running it in software rendering...

Try typing this: glxinfo | grep rendering
in the console.
If it gives you a no then i'm right and you should look here: [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto) and if it gives you a yes, well then i don't have any idea...

---

### Post by Inhumane on 2006-09-08
> **Izuil said:**
> I'm pretty much a noob at Linux and all this but I would guess you're running it in software rendering...

Try typing this: glxinfo | grep rendering
in the console.
If it gives you a no then i'm right and you should look here: [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto) and if it gives you a yes, well then i don't have any idea...

It gives me a yes :(, it seems to just be mouse-keyboard lag but I don't understand why/how to solve it

---

### Post by chocomoojuice on 2007-02-27
I was surfing the forums for this issue, and was surprised to find only 1 post about it.  Does anyone else have this problem?  It's as if whatever I do with my mouse, it's delayed 5 seconds before any action takes place (i.e., I move the mouse right, the cursor moves to the right 5 seconds later).  I've had this experience in two native linux games thus far: nexiuz and et.  I'm using the ATI Proprietary driver if that's of any consilation...:confused:

---

### Post by Mongoose on 2007-02-28
"Plays best on Nvidia."  I've played ET on several generations of Nvidia cards fine.  Remember ET is basically Quake3 engine with more features.  If you have the same problems in Quake3 you'll have more in ET.   That said you'd have to have a pretty slow GPU not to push ET.

---

### Post by rossjman1 on 2008-06-18
I have the same problem. The keyboard seems fine, but the mouse lags about a half a second in the game. I am using the ATI accelerated graphics driver and disable compiz before launching the game. It runs fine in Windows. What gives?

---

### Post by frodon on 2008-06-20
Delete your .etwolf directory then start ET, it will recreate it. In 90% of the cases it solves the issues, i had this mouse lag issue, deleted my etwolf and let ET recreate it and the problem was gone for good.

From my ET experience i know that from time to time your ET settings get messed up, either by the user or by downloading to much stuff from different servers, and the only thing that really fix it for good is to  recreate the .etwolf directory.

If you are used to play on a server and want to keep your levels and XP save your etkey in the .etwolf/etmain direcdtory, this file is the file that ET use to identify you on a server so backing it up then restore it on another install makes your previous identity restored.

---

### Post by rossjman1 on 2008-06-20
It worked! Thank you so much.

---

### Post by Username000 on 2008-06-23
i got this problem too but i dont have "etwolf" directory i have enemy-territory...



```
***********************************************************
 You are using software  (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode ()
Initializing OpenGL display
...setting mode : ....
Using XFree86-VidModeExtension Version ...
XF86DGA Mouse (Version ...) initialized
XFree86-VidModeExtension Activated at .....x....
Received signal 11, exiting...

"/home/user/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"




```



Whats wrong?

---

### Post by frodon on 2008-06-23
It's in your home directory, if you don't have one enemy territory will create it when you will start.
The $HOME/.etwolf directory is where ET put downloaded files needed to play on a server, it also contains your settings.

---

### Post by Username000 on 2008-06-23
> **frodon said:**
> It's in your home directory, if you don't have one enemy territory will create it when you will start.
The $HOME/.etwolf directory is where ET put downloaded files needed to play on a server, it also contains your settings.

Now i see my .etwolf directory...but i got another problem it dont start..
```

----- FS_Startup -----
Current search path:
/home/username/.etwolf/etmain
games/enemy-territory/etmain/pak2.pk3 (22 files)
games/enemy-territory/etmain/pak1.pk3 (10 files)
games/enemy-territory/etmain/pak0.pk3 (3725 files)
games/enemy-territory/etmain/mp_bin.pk3 (6 files)
games/enemy-territory/etmain

----------------------
3763 files in pk3 files
^3WARNING: profile.pid found for profile 'MYNAMEHERE' - system settings will revert to defaults
execing default.cfg
couldn't exec language.cfg
execing profiles/MYNAMEHERE/etconfig.cfg
r_smp is unsafe. Check com_crashed.
r_mode is unsafe. Check com_crashed.
r_depthbits is unsafe. Check com_crashed.
r_stencilbits is unsafe. Check com_crashed.
r_stereo is unsafe. Check com_crashed.
r_colorbits is unsafe. Check com_crashed.
r_texturebits is unsafe. Check com_crashed.
r_clampToEdge is unsafe. Check com_crashed.
r_ext_texture_env_add is unsafe. Check com_crashed.
r_nv_fogdist_mode is unsafe. Check com_crashed.
r_ext_NV_fog_dist is unsafe. Check com_crashed.
r_ext_texture_filter_anisotropic is unsafe. Check com_crashed.
r_ati_fsaa_samples is unsafe. Check com_crashed.
r_ati_truform_pointmode is unsafe. Check com_crashed.
r_ati_truform_normalmode is unsafe. Check com_crashed.
r_ati_truform_tess is unsafe. Check com_crashed.
r_ext_ATI_pntriangles is unsafe. Check com_crashed.
r_glIgnoreWicked3D is unsafe. Check com_crashed.
r_ext_compiled_vertex_array is unsafe. Check com_crashed.
r_ext_multitexture is unsafe. Check com_crashed.
r_ext_gamma_control is unsafe. Check com_crashed.
r_ext_compressed_textures is unsafe. Check com_crashed.
r_allowExtensions is unsafe. Check com_crashed.
r_glDriver is unsafe. Check com_crashed.
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
...setting mode .: .....
Using XFree86-VidModeExtension Version 2.
XF86DGA Mouse (Version ..0) initialized
XFree86-VidModeExtension Activated at .......
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (.)
Initializing OpenGL display
...setting mode : ....
Using XFree86-VidModeExtension Version ...
XF86DGA Mouse (Version ...) initialized
XFree86-VidModeExtension Activated at ...x...
Received signal 11, exiting...

```


if i try this "+set r_allowSoftwareGL 1" then it start but lags bad like if i move mouse then it take 5.sec or more to move...

EDIT: I did try delete etwolf directory but still didnt work...


Whats this?

"/home/username/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"






Whats wrong here?

---

### Post by frodon on 2008-06-24
ui.mp.i386.so is the binary handling the ET user interface so here maybe it is corrupted that's why deleting the .etwolf directory solve this kind of issue most of the time.

About your other error, have you installed your graphic driver ? I mean do you have direct rendering enabled ?

What do you get as answer to the folowing command :
```
glxinfo | grep rendering
```If it answers "direct rendering: No" then it is the priority to fix your graphic driver first.

---

### Post by Username000 on 2008-06-24
Got it work really thanks man...


but if i am in server then my default ping there is 50+  but it sometime go up too 300+..

---

### Post by frodon on 2008-06-25
Open the console in ET and type "/rate 25000" it shouls helps to get better ping if you have good connection.

You will find more infos about tweaking ET config to increase performances there :
[http://www.rtcw.jolt.co.uk/content/faq/et_scripts.html](http://www.rtcw.jolt.co.uk/content/faq/et_scripts.html)

---

### Post by Username000 on 2008-06-25
I got other problem i cant open console?..why?




Offtopic: What i need to install to open .so files?
if i try open .so file then it say:

"There is no application installed for this file type"

---

### Post by frodon on 2008-06-26
.so files are binaries, you can't edit them or install them, the game just need them at the right location.

For the console in ET maybe you have a keyboard issue, ET only recognize qwerty layout so sometimes some keys don't work as expected on other keyboards layouts (i use azerty myself).

What key/key combination have you tried.

---

### Post by Username000 on 2008-06-26
I use et default keys ...and got new problem if i play then some time brightness change ..(make it bad)...


qwerty

---

### Post by frodon on 2008-06-27
This is the common screensaver issue that we all have, either you disable the screenaver or put a longer delay so that it annoys you less.
Anyway when it arrives you can just go in the ET menu and move the brightness cursor it will immediately go back to normal.

---

