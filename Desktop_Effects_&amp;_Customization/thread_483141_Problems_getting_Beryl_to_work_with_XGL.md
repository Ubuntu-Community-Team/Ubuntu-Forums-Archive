---
title: "Problems getting Beryl to work with XGL"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by jcrow on 2007-06-24
I just got a new laptop and I am setting it up for work. I had no problems getting Beryl to work with my desktop which is a pentium 4 with Nvidia graphics. Unfortunately, the laptop is an AMD 64 X2 with an ATI card. I was able to follow the posts and install the correct driver and create an XGL session. I can log in with XGL and load Beryl and the gem is in the tray and it says Beryl is running, but it is not really running. With the XGL session I can enable desktop effects and they work fine (I got a message in the regular session that said that compositing was not available). If I select Beryl as the window manager with Desktop effects running nothing changes. Thanks for any help.

---

### Post by Ultra Magnus on 2007-06-24
If you want to run beryl, then you have to disable the desktop effects - Unfortunately I also have an ati card so i have to login to a separate session to be able to use the effects but it should work fine.

Actually a question - when you login with xgl does your screen go grey with a wierd curser before going to the desktop - I'd love to be able to use this as my default session but I don't want to because other people use my computer and I suspect they would worry if the screen went grey when they logged in

---

### Post by joe.turion64x2 on 2007-06-24
> **Ultra Magnus said:**
> If you want to run beryl, then you have to disable the desktop effects - Unfortunately I also have an ati card so i have to login to a separate session to be able to use the effects but it should work fine.

Actually a question - when you login with xgl does your screen go grey with a wierd curser before going to the desktop - I'd love to be able to use this as my default session but I don't want to because other people use my computer and I suspect they would worry if the screen went grey when they logged in
I too have an 'ATI laptop', a Radeon Xpress 1100 actually. Following some how to's in this forum helped me enable Beryl: I can not believe it could run that good with this graphics card!

I think I made the Beryl one my default session, and yes, it shows a gray screen for a moment (1 or 2 seconds only) but after that everything loads nicely.

Just make sure you lock the version of the Beryl packages in Synaptic, so Ubuntu won't try to update them with its XGL faulty versions.

Joe.

---

### Post by jcrow on 2007-06-24
I do get the wierd gray checkerboard during startup too. How you disable desktop effects? Just turning them off from the preferences tab does not work.

---

### Post by jcrow on 2007-06-24
I tried starting beryl from a terminal. this is what I got:



jcrow@jcrow-laptop:~$ beryl
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
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0
jcrow@jcrow-laptop:~$ 


any suggestions?

---

### Post by jcrow on 2007-06-24
I figured it out!!!!!

I uninstalled Beryl.  I reinstalled it following this method:
[http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29)

I then would get a white screen when I launched beryl. I fixed it with this:
[http://ubuntuforums.org/showthread.php?t=477076&highlight=white+screen](http://ubuntuforums.org/showthread.php?t=477076&highlight=white+screen)
I will add the command to the startup menu and I should be set.

---

### Post by jcrow on 2007-06-24
Well it sort of worked. After a few minutes the widow decorator acted weird and beryl won't load at start up. Any suggestions?

---

