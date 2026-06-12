---
title: "no window boarders in compiz"
date: 2007-05-08
forum: Desktop Effects &amp; Customization
---

### Post by searayman on 2007-05-08
I am using compiz but have no window boarders...

---

### Post by Prometheum on 2007-05-08
I have the same problem; I'm using nvidias proprietary 9755 drivers on a GeForce Go 7 in an HP Pavillion dv2k laptop. I have everythign fine in metacity, but if I use compiz or beryl I lose window borders, but nothing else apparently. My theme is set up properly (I think) but I'm not sure. Any help would be appreciated.

---

### Post by dionisi on 2007-05-09
i got the same problem, no border, when i open a page or smth else it doesnt have the up border where it shows the minimaiz maximaiz ot close the window, everything else works fine like cube and other beryl settings only this is the problem.
btw it happens when i enable the 3d effects so i guess is not a beryl problem
any help
thnx

---

### Post by Ateo on 2007-05-09
I have the same issue but only when I upgraded to compiz 0.5.0 while running emerald (for compiz [from this thread]("http://ubuntuforums.org/showthread.php?t=423743")). Are you using a similar setup?

---

### Post by Prometheum on 2007-05-09
GTK-window-decorator isn't running on my system before I launch beryl/compiz, if that's what you're implying.

Has anyone else encountered a fix for this problem? Maybe a bug should be posted, if one isn't already.

---

### Post by vradovic on 2007-05-09
I have same problem!

No window border and no title bar.
Nvdia drivers installed

---

### Post by Ateo on 2007-05-09
> **Prometheum said:**
> GTK-window-decorator isn't running on my system before I launch beryl/compiz, if that's what you're implying.

Has anyone else encountered a fix for this problem? Maybe a bug should be posted, if one isn't already.

It's not gtk-window-decorator that you need to be looking for in sessions. It's metacity.

I encountered this issue when I had the wrong libdecoration0 version installed while I tested compiz 0.5. I removed that, installed the correct version and had working window borders again.

---

### Post by vradovic on 2007-05-09
how you do that?
witch version is right one ?

explain please.

Regards

---

### Post by vradovic on 2007-05-09
edit your xorg.conf 
/etc/X11/xorg.conf


IN Screen section add this!

Option "AddARGBGLXVisuals" "True"
DefaultDepth 24

---

### Post by Ateo on 2007-05-09
> **vradovic said:**
> how you do that?
witch version is right one ?

explain please.

Regards

First question is have you at any point upgraded compiz to 0.5.0. If not, then ignore me.

---

### Post by prrawls on 2007-05-10
> **vradovic said:**
> edit your xorg.conf 
/etc/X11/xorg.conf


IN Screen section add this!

Option "AddARGBGLXVisuals" "True"
DefaultDepth 24


This fixed the issue for me!  Thank you!

---

### Post by dionisi on 2007-05-10
> **vradovic said:**
> edit your xorg.conf 
/etc/X11/xorg.conf


IN Screen section add this!

Option "AddARGBGLXVisuals" "True"
DefaultDepth 24


this is correct, for me it worked

---

### Post by Prometheum on 2007-05-10
> **vradovic said:**
> edit your xorg.conf 
/etc/X11/xorg.conf


IN Screen section add this!

Option "AddARGBGLXVisuals" "True"
DefaultDepth 24

This fixed everything in beryl; Compiz has problems, but I have a titlebar (and my compiz options are probably just weird) 

In conclutsion, thanks, this works great!

---

### Post by anholtz on 2007-05-12
I too am having the window bar disappearance problem.  This only happens with Compiz and Beryl (not with Metacity).  I have added suggested lines to the xorg.conf file and still do not have any results. Also, I have messed with the rendering path options as well as turning off all effects in beryl in an attempt to isolate the problem.  Finally, I have "removed completely" all beryl and emerald related files from the synaptics package manager and reinstalled.  Are there any other suggestions?

Below show the xorg.conf modifications:

```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    Option "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "nvidia-auto-select +0+0; 800x600 +0+0; 640x480 +0+0"
    Option "AddARGBVisuals" "True"
    Option "AddARGBGLXVisuals" "True"
	SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    	EndSubSection
EndSection
```

Are there any troubleshooting commands I should use to record what happens in the terminal when I switch from Metacity to compiz/beryl?

Thanks

---

### Post by churchi on 2007-05-12
> **vradovic said:**
> edit your xorg.conf 
/etc/X11/xorg.conf


IN Screen section add this!

Option "AddARGBGLXVisuals" "True"
DefaultDepth 24

absolutly spot on. this fixed my problem right away.

does anyone know why this fixes the issue straight away?

cheers

---

### Post by atari05 on 2007-05-16
> **vradovic said:**
> edit your xorg.conf 
/etc/X11/xorg.conf


IN Screen section add this!

Option "AddARGBGLXVisuals" "True"
DefaultDepth 24

Serously, how did you dig this up, This is option makes 0 sense :|


it works and I'm totally happy but...wow, I would of never of guessed this would be the root of he issue!!!

---

### Post by short4lif2 on 2007-05-17
> **atari05 said:**
> Serously, how did you dig this up, This is option makes 0 sense :|


it works and I'm totally happy but...wow, I would of never of guessed this would be the root of he issue!!!

> **vradovic said:**
> edit your xorg.conf 
/etc/X11/xorg.conf


IN Screen section add this!

Option "AddARGBGLXVisuals" "True"
DefaultDepth 24



Ok at first this did not work for me, and for those of you in the same position, all is not lost, this will help!  Add these changes to your xorg, and then save it.  Restart or log out then in.  After that go to system>administration>restricted drivers manager.  Disable NVIDIA accelerated graphics driver by unchecking the box under "Enabled."  Then recheck the box, and wait for the computer to finish reinstalling the driver for you.  Restart your machine, and install compiz.  Then enable it.  That should do it.  -Note if you have dual monitors set up, reinstalling the NVIDIA drivers will disable dual monitor support.  All you have to do is go to a console and type in

sudo nvidia-settings

then just enable dual monitors like you did before the re-install.  Another note- the reinstall may have made some changes to your xorg.conf.  Just go in, and add the above changes mentioned by Atari.  Hope that helps!  this took me about a week of passive poking around.  Enjoy!

---

### Post by lolwhites on 2007-06-22
hi short4lif2

I'm having the same problem as you. When I tried your solution it wouldn't let me uncheck the box - I get this message:
> Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid or does not exist (it does)

---

### Post by short4lif2 on 2007-06-22
Hey that's not right is it! haha.  Check your permissions for the xorg.conf file and make sure that is accessible to everyone.  i dunno why i feel like that has something to do with it.  Otherwise i have no idea, i know too little about linux to really figure that out for you.  Just make sure that xorg is accessible and read it over really carefully for typos.  also look through your nvidia-settings to make sure that everything is ok.

---

