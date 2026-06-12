---
title: "Help with Beryl problem"
date: 2007-03-23
forum: Desktop Effects &amp; Customization
---

### Post by Heedbanger on 2007-03-23
Hi

I am having a problem with beryl i installed it yesterday and it seemed to be working fine.  But now when I start beryl manager nothing happens, the beryl manager runs and I have no error messages in the terminal, but have no wobbly windows or anything anymore.  I typed beryl in the terminal and got the following: 

dave@heedbanger:~$ beryl-manager
dave@heedbanger:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: No GLXFBConfig for default depth, falling back on visinfo.
Reloading options
No framebuffer_object support! (only simple Blur aviable).


After which the windows are wobbly when i move them but none of the other effects are working.  I also am getting the windows borders missing problem sometimes usually after I close a window.  Everything seemed to work fine after i first installed i just typed beryl-manager in the terminal and it worked ok.  

I hope someone can help me to fix this.

---

### Post by pkslot on 2007-03-23
I had almost the same problem, and my windowdecoration was missing too.

I read that the graphics should be 24 bit, so i edited the xorg.conf file
> sudo gedit /etc/X11/xorg.conf
changing to 24 bit, everywhere it said 16. I saved, exit, Pressed Ctrl + Alt + Backspace, and it worked perfectly.

Remember to make a backup file of the xorg.conf before editing!!!
This should do the trick:
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

I can't promise that it'll work for you, but it's worth a try ;)

NOTE: I probably should mention, that i'm running beryl on an 700mhz AMD Duron, Nvidia GeForce2 MX/MX 400 (32 mb ram), 512 mb sdram.

---

### Post by pkslot on 2007-03-23
Any results?

---

### Post by Heedbanger on 2007-03-24
My depth was already set at 24.  So that wasn't the problem but I managed to find the solution I had to add:

Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True" 

I had to add those 2 lines in the screen section of the config file and that solved the problem.  You have to use those lines when you use the latest nvidia drivers rather than the nvidia-glx from the repos.

---

### Post by Derspankster on 2007-03-24
Thanks for the tip. It was just what I needed.

---

