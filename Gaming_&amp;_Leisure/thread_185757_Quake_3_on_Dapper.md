---
title: "Quake 3 on Dapper"
date: 2006-06-01
forum: Gaming &amp; Leisure
---

### Post by SyntaxTerror on 2006-06-01
Hey guys,

I'm having some trouble getting q3 up and running on Dapper.

When I run it I get the following output:

```

Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/ian/.q3a/baseq3
/usr/local/games/quake3/baseq3/tig_ra3.pk3 (125 files)
/usr/local/games/quake3/baseq3/ra3sgmap2.pk3 (186 files)
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3/map-ma_nate1.pk3 (41 files)
/usr/local/games/quake3/baseq3/charonra3map1.pk3 (27 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
4452 files in pk3 files
execing default.cfg
execing q3config.cfg
execing autoexec.cfg
execing syntax.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading opengl32: QGL_Init: Can't load opengl32 from /etc/ld.so.conf or current dir: /usr/local/games/quake3/opengl32: cannot open shared object file: No such file or directory
failed
...loading libGL.so.1: Initializing OpenGL display
...setting mode 6: 1024 768
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 1024x768
Couldn't get a visual
...WARNING: could not set the given mode (6)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

```

If I check fglrxinfo I get the following:

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

And glxinfo |grep render gives me:

```

direct rendering: Yes
    GLX_ATI_render_texture
OpenGL renderer string: RADEON 9600 XT Generic

```


As far as I can tell, fglrx is all up and running, yet the game still tells me failed to load openGL sus system.

Are there any additional packages I've missed?  I can't see what I'm missing here.

---

### Post by BungaMan on 2006-06-01
This is absolutely a guess but from looking at the warnings it doesn't seem to be able to switch to certain resolutions like 1024x768 and 640x480.  Are they defined in your xorg.conf?

---

### Post by tribaal on 2006-06-01
Not directly related to your concern, but anticipating a possible future problem:
I installed Q3 on Dapper this afternoon, and I had problems with the sound (no sound at all): the fix is to set read/write access to your sound device (the /dev/* stated when the game start).

Sorry if this doesn't help at all, but I've spent hours figuring this out, hopefully it will save you the trouble...

Good luck with the resolution :(

- trib'

---

### Post by macmasterxiv on 2006-06-01
Well, first of all, unless you really need punkbuster you shouldn't use 1.32b on a modern linux distrobution. icculus.org/quake3 is a much better and more linux friendly client with sound working natively and many bugfixes over 1.32b

---

### Post by SyntaxTerror on 2006-06-01
macmasterxiv I play extensively online (at least 4 hours a night), so pb is a must.

I worked out my problem.  After being able to successfully install and play Q4 and ET, I worked out that there's no way it could be my fglrx or X setup.

After hours of mucking around I worked out it was my RA3 config which was doing it - I run a very heavily tweaked config (the game looks worse than Doom 1!)

I deleted to configs out of baseq3 first, and the game loaded, but the mod wouldn't.  So I deleted the cfgs out of the arena directory, and the problem still occured, this had me worried as I thought it must be the mod that was stuffed...

It turns out I'd completely forgotten the cfgs which get copied across in to ~/.q3a when you play the game.  As soon as I deleted these as well the game worked fine!

So I put my config back and commented out all lines which changes cvars starting with "r_".  Success!  It works!  By this time I was way too early in the morning for me to continue.  But tonight when I take another look at it I will one by one uncomment the r_ lines and see which one is the culprit.

My initial feelings was that it would be r_texturemode (I have a toggle bind to switch between two different r_texturemodes), but this wasn't the case.

Thanks for the input guys, I guess it serves me right for sticking my config in there without seeing if things *just work* firstly.  I could've saved myself a whole day of stuffing around.

---

### Post by lexxonnet on 2006-06-01
Actually, I think it cant find your opengl renderer. Try symlinking your opengl libraries to the quake directory. I remember getting similar messages and that was what finally worked for me...

```

ln -s /usr/lib/libGL.so.1 /usr/local/games/quake3/libGL.so

```

---

### Post by SyntaxTerror on 2006-06-01
Hi mate,

That's also one of the things I tried in trying to get it to work.  After linking the neccessary libraries it was still giving similar results.  It was most definately one of the r_ cvars I've set in my config.  I'll eliminate which one specifically it is tonight when I get home and post it here for future reference.

---

### Post by lexxonnet on 2006-06-01
Fair enough :)
Well... glad you got it working though! 

Cheers,
Lex

---

### Post by SyntaxTerror on 2006-06-02
Well after hours of commenting cvars out of my config one by one and retrying I finally struck gold...

I had:
```
seta r_depthbits "32"
```

This was causing my crashes.  Game runs fine with it commented out.

I hope this reference point saves someone else hours of pulling their hair out.

Happy fragging guys!

---

### Post by lexxonnet on 2006-06-02
Cheers mate... I'll watch out for that one when I get confident enough to start playing around with the settings ! :)

---

### Post by almostlinux on 2008-04-28
> **SyntaxTerror said:**
> Well after hours of commenting cvars out of my config one by one and retrying I finally struck gold...

I had:
```
seta r_depthbits "32"
```This was causing my crashes.  Game runs fine with it commented out.

I hope this reference point saves someone else hours of pulling their hair out.

Happy fragging guys!

That saved me 2 hours. Thanks :)

---

