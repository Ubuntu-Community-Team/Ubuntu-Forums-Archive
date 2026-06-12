---
title: "Desktop Effect only avaliable in low resolution"
date: 2008-06-20
forum: Desktop Environments
---

### Post by alpheusladesa on 2008-06-20
Hi I'm currentle trying to install Compiz fusion on my computer.
I'm using a 8600GT card and I installed the nvidia driver for it (Nvidia-glx)
The strange thing is after installing the driver I was unable to get desktop effects to work ("Desktop Effect cannot be enabled) and neither can I find my driver settings.
Whenever I press System Tools>Nvidia Driver settings it says I haven't installed a Nvidia driver yet.

Sometimes when I start up it'll boot up in 800x600 instead of 1024x768 and that's the only time I can enable Desktop Effects...(I installed nvidia-glx-new before but the low resolution caused me to uninstall the package and tried nvidia-glx)

This is what I get when I type in "compiz --replace"

Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

I'm running Ubuntu 8.04 (Hardy Heron)
If you have any doubts about something please just ask me cuz I spend hours trying the solve the problem and I might not remember some details I just described correctly.

Thank you for your help!!

---

### Post by Happy_Man on 2008-06-20
Hm, when you say "nvidia-glx" you do mean the correct version for your card, right? "nvidia-glx-new"? Not the actual "nvidia-glx" package, which is for old old Geforce MX cards, right?

---

### Post by alpheusladesa on 2008-06-21
No I mean the "Nvidia-glx" package cuz I installed glx-new before and there is where the problem came from. (Low resolution but desktop effect works)
Also when I use /etc/x11/xorg.config to configure my resolution instead of giving me what most people get (Straight to video card options) I get a bunch of questions on Keyboard styles...:(

BTW now my computer run in 1024x764. (No driver detected and no card detected)

---

### Post by alpheusladesa on 2008-06-21
Anyone help please? I did a lot of searching on the internet but seems like I'm having many problem at once...

---

### Post by Happy_Man on 2008-06-21
Well, you're going to have even less luck with nvidia-glx, so get nvidia-glx-new back on there, please. Doing some googling, it seems that Hardy seems to be a bit touchy with 8600GT cards, so maybe, for now, you can try some other way to get Desktop Effects running.

---

### Post by pietjanjaap on 2008-06-22
I think your drivers are not installed ok, or your videocard,monitor is not detected ok.
Try this:

But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the x,
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

With envy you can remove/install ati and nvidea drivers, also in textmode , so check envy website.

---

### Post by alpheusladesa on 2008-06-24
Ok thanks for the help. I'll try and post my result~:)

---

### Post by alpheusladesa on 2008-06-27
Alright~ in order to prove I haven't screw anything up yet, I did a new fresh install again. I used EnvyNG to install the Nvidia driver and it worked like a charm~~ When I restarted my computer...The effects work but the resolution is set to 600*480 and I can't run the xserver-xconfig thing because it ask me about my keyboard layout (What the....) and then after a certain step (Still in the keyboard thing) it jumps out with a "xserver-xorg postinst warning" (It's weird because it worked for most people)
Yeah so I'm using the awesome effects but in a very low resolutions.

Can you give me some hint on why this is happening?

---

### Post by moshuptrail on 2008-06-28
You can look at the contents of /var/log/Xorg.0.log
It will tell you what's going on as the display fires up.
I had this same problem cuz it could not recognize my display and would not find a mode with the right hsync.   All modes were unavailable so it took some low-res default. 
I still don't have desktop effects either.
Still monkeying around.

---

