---
title: "Graphics Card in degraded mode"
date: 2010-09-08
forum: Desktop Environments
---

### Post by esclinux on 2010-09-08
I have an ATI Radeon card and everything seemed to be working fine until I moved the computer.  In doing so I bent one of the pins on the VGA connector when plugging it back into the card.  When the system booted it popped up a message indicating the system was running in a degraded graphics mode.  I hit the restart X option and everything appeared the same until I tried to run a game.  I found the bent pin and fixed that but I still am having a problem.  When running the game I get the following messages:  



-------- [Loading Renderer] ---------
Initializing OpenGL display
...setting mode 3: 1024 768
Using XFree86-VidModeExtension Version 2.2
Xlib:  extension "GLX" missing on display ":0.0".
Error couldn't get an RGB, Double-buffered, Depth visual, Stencil Buffered
Xlib:  extension "GLX" missing on display ":0.0".
Error couldn't get an RGB, Double-buffered, Depth visual
ref_gl::R_SetMode() - invalid mode
Initializing OpenGL display
...setting mode 3: 1024 768
Using XFree86-VidModeExtension Version 2.2
Xlib:  extension "GLX" missing on display ":0.0".
Error couldn't get an RGB, Double-buffered, Depth visual, Stencil Buffered
Xlib:  extension "GLX" missing on display ":0.0".
Error couldn't get an RGB, Double-buffered, Depth visual
ref_gl::R_SetMode() - could not revert to safe mode
ref_gl::R_Init() - could not R_SetMode()
Master server at 174.37.203.131:27900
Sending shutdown to 174.37.203.131:27900
recursive shutdown
Error: Couldn't initialize renderer!


I'm running Ubuntu 10.4

Is there something I need to reload or is it possible that the card is now damaged?  Any help would be greatly appreciated.

---

### Post by dirty_harry on 2010-09-09
Did you try to replace your video cable? 

And are you using VGA or DVI?

---

### Post by esclinux on 2010-09-09
The cable is a dedicated one.  It is attached to the monitor (old monitor) and cannot be replaced.
 
I'm using the VGA output of the video card.
 
I had initially loaded the system with an Nvidia card in the system and then installed this ATI card that had more RAM.   It worked fine up until the bent pin incodent??  I went back to the Nvidia card and everything seemed to work.  I put the ATI card back in and still have the problem?  
 
Thanks

---

### Post by dirty_harry on 2010-09-09
What graphics card are you using? Drivers? 

Honestly, I have no clue how to help you. This seems to be a hardware problem, but I have no idea what causes the error. :-k

Do you have a second monitor to try with? Maybe this could be of help.

---

### Post by esclinux on 2010-09-09
It is an ATI Radeon 9600??  128 Mb RAM.  using the radeon driver but the sytem picked that up I didn't have to add it althought I did reinstall them based on an article on this forum.  There is a proprietary driver that ATI provides that I have not tried yet.  I was going to try that and see if it made a difference fglrx I think?
 
I have another monitor I can try and I'll check that out later when I get home??  It does seem to be HW related but I can't understand it either.  
 
Thanks for looking.

---

### Post by dirty_harry on 2010-09-09
That's funny. I have a Radeon 9600SE too. The current amd/ati driver doesn't support this card! And for older version you need to have a older Xorg version too. 

A few weeks ago I gave up and bought an old geforce, because of this... 


###
You're welcome & Have a nice day

---

### Post by esclinux on 2010-09-09
Funny, yes, I was looking at buying a new card today as well.  What card did you get?
 
It is wierd though because I was using it before and did not have these problems?
 
Thanks

---

### Post by dtfinch on 2010-09-09
I think the "Restart X" option disregards whatever you may have had in xorg.conf, and relies on auto-detection instead. If you've ever edited it manually (or used that nvidia configuration tool), that could explain the degraded graphics, followed by it seeming to work after restarting X, minus 3D support.

---

### Post by dirty_harry on 2010-09-09
[B]@esclinux
[/B]You had a nvidia card installed which was replace by an ati radeon 9600. This one worked just fine out of the box? I highly doubt. Anyway, after you moved your system physically and the pin was bend back and forth the radeon 9600 showed the quoted error while loading a game. Now you have reinstalled the old card?

I had several problems with my AGP ATI radeon 9600SE. I tried the free radeon driver but gave up after a while... I bought a used AGP Geforce 7600GT, which will be the last piece of hardware for this system. The next thing will be a new low-budget-system around 100&#8364;... I am still struggling with the 7600GT ;)

**@dtfinch**
What do you mean with "Restart X" option. If he hasn't made any changes apart from moving it how would this affect the xorg-configuration? Or is xorg.conf also changed when a new card is installed(I mean ATI out, NVIDIA in)

---

### Post by dtfinch on 2010-09-09
I'm saying if he had an nvidia-specific xorg.conf, the reason it would fail to initialize at each boot but then succeed when he chooses "Restart X" is because when it restarts X it has it disregard xorg.conf and rely on autodetection, or at least that has always been consistent with in my experience with 10.04, requiring me to exit to console login and restart X manually when I don't want it to fallback to autodetection.

---

### Post by dirty_harry on 2010-09-09
Ok, that's new to me.  So when I restart my desktop-session xorg.conf is ignored?

And this "restartx" is also quite strange. "service gdm restart/start/stop" is what I use to restart my xubuntu currently. Does this also bypass xorg.conf?

Oh, I think I get it:
gui fails, error message appears, option is "Restart X" and bamm here we go?

Bueno, maybe it's time for me to get some sleep. 8) Sorry for the misunderstanding.

---

