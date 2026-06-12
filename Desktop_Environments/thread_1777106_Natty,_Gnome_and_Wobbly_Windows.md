---
title: "Natty, Gnome and Wobbly Windows"
date: 2011-06-07
forum: Desktop Environments
---

### Post by danduq on 2011-06-07
Upgraded to 11.04, tried Unity for a month but hated it, reverted back to Gnome today, now I have no wobbly windows.  :(

I've enabled WW in CCSM and all the settings are defaulted. I've tried removing all traces of Unity using synaptic, but it just doesn't seem to have made a difference.

I've read a few threads about this, but so far haven't seen a fix other than "it just started working", so any pointers or ideas would be great as it hasn't just started working for me.

Dell Latitude D620 with current nVidia proprietary driver installed.

Cheers!

---

### Post by danduq on 2011-06-14
Bump! Still no wobbly windows.  :(

---

### Post by Khakilang on 2011-06-14
Have you try Ubuntu Tweak? That may help.

---

### Post by danduq on 2011-06-14
Just gave Ubuntu Tweak a try and it hasn't helped. Tried toggling "Enable wobbley windows" but no difference. Thanks for the suggestion though.

---

### Post by stinkeye on 2011-06-14
Sure your not running metacity.
Try alt+F2 
```
compiz --replace
```

---

### Post by danduq on 2011-06-20
I tried running the compiz --replace command, but each time I did it locked up my PC and restarted GDM, so I don't think it ever 'took'.

I have since switched back to running Unity. It has a few things I don't like, but I'll put up with them for now and hopefully they'll be addressed in future releases.

Thanks for your help.

---

### Post by stinkeye on 2011-06-20
Ok.
Just if your curious, you can install wmctrl to check what window manager is running.
```
sudo apt-get install wmctrl
```

Then run 
```
wmctrl -m
```
to show what WM is running.


eg my output
```
glen@Natty:~$ wmctrl -m
Name: **Compiz**
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: OFF
```

---

### Post by danduq on 2011-06-20
Ah, that's useful, thanks!

---

### Post by 23dornot23d on 2011-06-20
Try this too ..... it may just show some more information that may be useful to others.

**/usr/lib/nux/unity_support_test -p**

Here is my output from the command above ( just cut and paste into a terminal )

> 
keith@keith-MS-7181:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9300M GS/PCI/SSE2
OpenGL version string:  3.3.0 NVIDIA 275.09.04

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
keith@keith-MS-7181:~$ 
hope it helps in some way ..... 

( I realize you are now not trying to run UNITY but this one command does a lot of things quickly too )

---

### Post by danduq on 2011-06-20
Thanks, now that I'm running Unity it's showing;

$ /usr/lib/nux/unity_support_test -p
Warning: UNITY_FORCE_START enabled, no check for unity or compiz support.

Oh, that's because I've got an nvidia card and cannot get unity to work unless I roll back to the previous nvidia driver and set UNITY_FORCE_START. Either that or use Unity2d.

---

### Post by danduq on 2011-06-21
OK, so I got fed up with Unity again and decided to switch back to classic, but lost my wobbly windows again. So, from previous comments;

```
$ wmctrl -m
Name: Metacity
Class: N/A
PID: N/A
Window manager's "showing the desktop" mode: N/A

```

So it seems like I am using Metacity for some reason.

Now, when I run compiz --replace in a terminal, everything starts working again! BUT the terminal sits at > Setting Update "map_effect" and doesn't end. If I ctrl+c it, I get a segmentation fault.

Any ideas how I can proceed from here?

Thanks!

---

### Post by stinkeye on 2011-06-21
Press alt+F2 and run ```
compiz --replace
``` from there.

---

### Post by danduq on 2011-06-21
Thanks Stinkeye, but this results in my screen freezing completely. I am still able to move the mouse pointer around, but nothing else. I have to then go to another terminal (or tty, or whatever it's called when you do ctrl+alt+F1) and do a gdm restart.

---

### Post by stinkeye on 2011-06-21
If you have the proprietary drivers installed and compiz won't run
I'm afraid there is little I can help you with.
For me I had no problems with a Nvidia GeForce 9400GT running driver version 270.41.06

---

### Post by danduq on 2011-06-21
That's just it. Before I upgraded to 11.04 and Unity, it all worked fine, so I know the combination of my graphics card, driver, compiz and gnome are compatible.

Thanks for your help though. I will keep soldiering on.

---

### Post by danduq on 2011-06-22
OK, this is beginning to drive me crazy. I cannot get compiz to run in Gnome and I can't get any errors out of it. When I run the compiz --replace command, my windows rearrange themselves and then freeze. The mouse pointer can move around, but I can't do anything. I have to do a gdm restart, which of course then restarts Gnome with Metacity.

I have tried removing all Unity stuff, reinstalling gnome, reinstalling compiz, reinstalling ubuntu-desktop. Nothing seems to work.

Any ways that I may be able to troubleshoot this would be appreciated. Unity has been doing my head in and I don't think I can use it without putting a foot through my monitor.

---

