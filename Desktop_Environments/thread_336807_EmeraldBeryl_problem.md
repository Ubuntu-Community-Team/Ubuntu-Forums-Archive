---
title: "Emerald/Beryl problem"
date: 2007-01-12
forum: Desktop Environments
---

### Post by sovereign_soul on 2007-01-12
As per the instruction listed at [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX),
I installed beryl and the emerald themes. However, everytime I run the beryl-manager, windows loose their borders/tittle-bars. 
when beryl-manager is run from the command prompt, it gives this error - 

neo@zion:~$XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present

** (process:6113): WARNING **: get_setting_is_integrated not found in backend ini

** (process:6113): WARNING **: get_setting_is_read_only not found in backend ini

** (process:6113): WARNING **: get_setting_is_integrated not found in backend ini

** (process:6113): WARNING **: get_setting_is_read_only not found in backend ini
Initiating splash
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32

Other than this beryl works well; 3D desktop,rotation,wobbly windows --all these work fine.
I have nvidia GeForce7400 with 1.0.9746 driver on HP notebook.

I've been searching the net for solution for the past 2 hours](*,)  but no success till now. Please suggest any possible solution to this problem.

Thanks

---

### Post by klep on 2007-01-12
I get the impression I know even less about all this than you. but have youy tried installing nvidia-glx?

sudo apt-get install nvidia-glx

---

### Post by dabl on 2007-01-12
Sov, you undoubtedly have some version of the famous "missing window decorations" problem.  If you got so far as having the red Beryl gem on your taskbar, pop it up and choose the fourth item on the menu list, "Select Window Manager".  Change it to GDK or Gnome or KDE or whatever you were using before.  Then click the third menu item, "Reload Window Manager".  At this point, you should be back to working window borders.  Then, search this forum or Google "Beryl Window Decorations" or something like that, and you should find a lot about this issue.

BTW, I run Kubuntu Edgy and found that the combination of the latest Nvidia driver and the new Beryl won't work with the Aquamarine window decorator -- it blows up my taskbar.  So there's reason to suspect that you can get too much of the latest software together and it is not stable on some hardware platforms.

Good luck with it!:cool:

---

### Post by quoick on 2007-01-12
I am a million miles from being an expert but with an Nvidia card, you may want to install beryl without AIGLX. I have installed using the Nvidia drivers using the guide found at [http://ubuntuforums.org/showthread.php?t=263851]("http://ubuntuforums.org/showthread.php?t=263851") and it has been running sweet. Try the first option when installing the Nvidia drivers (lupine repo).

---

### Post by robgill on 2007-01-12
> **sovereign_soul said:**
> As per the instruction listed at [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX),
I installed beryl and the emerald themes. However, everytime I run the beryl-manager, windows loose their borders/tittle-bars. 
when beryl-manager is run from the command prompt, it gives this error - 

neo@zion:~$XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present

** (process:6113): WARNING **: get_setting_is_integrated not found in backend ini

** (process:6113): WARNING **: get_setting_is_read_only not found in backend ini

** (process:6113): WARNING **: get_setting_is_integrated not found in backend ini

** (process:6113): WARNING **: get_setting_is_read_only not found in backend ini
Initiating splash
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32

Other than this beryl works well; 3D desktop,rotation,wobbly windows --all these work fine.
I have nvidia GeForce7400 with 1.0.9746 driver on HP notebook.

I've been searching the net for solution for the past 2 hours](*,)  but no success till now. Please suggest any possible solution to this problem.

Thanks

Before you try installing anything else/etc try running it as
```
beryl-manager && emerald --replace
```
That works for me.

---

### Post by mrzippy on 2007-01-12
I am having a similar issue, but if I scale the windows the decorations are there, just it puts them under the top panel...

I it did work at one stage, then I had to run beryl with sudo, now that doesn't work either...

Odd as I haven't changed anything :(

Intel graphics here GMA 900

---

### Post by sovereign_soul on 2007-01-13
](*,) 

Still no luck ... any more suggestions ?

---

### Post by zamphier on 2007-01-14
I had the same problem when trying to run Twinview w/ the same error code.
For me it was the inclusion of:
Option         "AddARGBGLXVisuals" "True"	
and
 Option	   "AllowGLXWithComposite" "True"
in the screen section of xorg.conf

---

### Post by ikari899 on 2007-01-21
i am having very close to the exact same problem i have tried all the fixes listed here and none of them seem to help.  maybe i am over looking some thing here is what is on the terminal after entering beryl-manager && emerald --replace

XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
Reloading options
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
Initiating splash

every thing seems to be working fine besides the lack of menu bars.  and when i reopen the terminal there is just nothing in it.  it is simply a blank box. all other programs open but have no menu bars.

---

### Post by ikari899 on 2007-01-22
ok well i found a fix for my problems.  it is that:

Option "DisableGLXRootClipping" "True"
Option "AddARGBGLXVisuals" "True"

must go under the DEVICE section!!!
most guides tell you to put it under the screen section, but i do have it under the screen section as well just to make sure.

i also changed the default depth to 24 instead of 16

now i would like to say this removed all my errors but it did not.  i am now encountering the black screen issue. odd considering i have a 128MB card...

---

### Post by sovereign_soul on 2007-01-29
^^^^ Worked for me too . Thanks dude !:D

---

