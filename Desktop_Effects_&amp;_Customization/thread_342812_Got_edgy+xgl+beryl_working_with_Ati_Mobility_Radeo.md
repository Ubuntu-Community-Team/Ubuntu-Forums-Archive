---
title: "Got edgy+xgl+beryl working with Ati Mobility Radeon X1600"
date: 2007-01-20
forum: Desktop Effects &amp; Customization
---

### Post by happis on 2007-01-20
After at least 10 hours of trying I finally did it, got beryl working on my computer. Here's my hardware:

Acer Travelmate 8204WLmi with Ati Mobility Radeon X1600

Here's how i did it:

First I installed fgrlx drivers with this guide using method 2:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C")

Then, I installed XGL with this guide (Beryl installed this way didn't work, so don't install beryl yet):
[http://wiki.cchtml.com/index.php/XGL-Ubuntu]("http://wiki.cchtml.com/index.php/XGL-Ubuntu")

After logout and login fonts were too big and reboot and shutdown buttons were missing from the exit window of gnome, so I had to modify my /usr/local/bin/startxgl.sh file to look like this:
```
#!/bin/sh
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer -dpi 96 &
sleep 2 && DISPLAY=:1 
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie" 
exec gnome-session
```

Finally, I installed Beryl from SVN snapshots repository with this guide:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_from_the_SVN_snapshots_repository]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_from_the_SVN_snapshots_repository")

Hopefully someone finds this post useful.

---

### Post by thommym on 2007-01-30
If you could get me going it would be greate. I've a Acer Ferrari 5000 also with ATI Mobility Radeon X1600. Trying Edgy Eft AMD64 Safe Display mode install but the screen is just a blur.

Isn't the a text based install for Ubuntu or am I better off with another dist?

Have also tried Edgy Eft on a NVIDIA GeForce 8800GTX with a AMD Athlon AM2 which also
fails to provide a working screen. :confused:

---

### Post by rodrosenberg on 2007-02-12
I'm going to give this a try I've had trouble getting my driver working using the automatic install

Thanks

Rod

---

### Post by chalewa on 2007-02-12
> **thommym said:**
> If you could get me going it would be greate. I've a Acer Ferrari 5000 also with ATI Mobility Radeon X1600. Trying Edgy Eft AMD64 Safe Display mode install but the screen is just a blur.

Isn't the a text based install for Ubuntu or am I better off with another dist?

Have also tried Edgy Eft on a NVIDIA GeForce 8800GTX with a AMD Athlon AM2 which also
fails to provide a working screen. :confused:



you are trying to install ubuntu or you already have that installed?

---

### Post by shareMenaPeace on 2007-02-12
On a sidenote when you run beryl and set beryl settings allready you might find uninstalling beryl to default values difficult.

In this case try my small how to reinstall beryl (if you run it before successful).
Also i posted a few recommended settings and shortcuts.

Cheers

---

### Post by contro on 2007-02-16
[[IMG]http://aycu01.webshots.com/image/10240/2004820498316938342_rs.jpg[/IMG]](http://allyoucanupload.webshots.com/v/2004820498316938342)

I could not get that command to work. The file is saved to the desktop do I have to save it somewhere else or am I doing something wrong.

---

### Post by cephlon on 2007-02-18
I have the Acer Aspire with X1600 and XGL and Beryl are running great. I just followed this guide:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

When I first attempted to install Beryl I accidentally followed the Aiglx guide, which didn't work out to well.

---

### Post by contro on 2007-02-19
> **cephlon said:**
> I have the Acer Aspire with X1600 and XGL and Beryl are running great. I just followed this guide:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

When I first attempted to install Beryl I accidentally followed the Aiglx guide, which didn't work out to well.

How did you install the ATI graphics drivers or did you just follow the guide after installation of unbuntu?

---

### Post by Frazer on 2007-02-19
It worked for me :) thanks for this post.  Iv been trying forever too lol

Im on the hp nc8430 with a mobility ATI x1600

EDIT:

It just broke after updating with the ubuntu updater.

when i use my beryl session I just get a white screen after the splash screen.

Here is the output of some commands.

scottf@scottf-laptop:~$ beryl
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
scottf@scottf-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Generic
OpenGL version string: 2.0.6286 (8.33.6)

scottf@scottf-laptop:~$ lspci | grep 'ATI'
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c5
scottf@scottf-laptop:~$

---

### Post by de_RiN on 2007-02-27
I have exactly the same problem : (

X1600 Ati mobility on HP nc8430

Too bad I did never see it work, I updated before I had the chance.

This is what I took from /var/log/Xorg.0.log. maybe this is giving some information needed to help us solve the problem?

> 
(II) fglrx(0): VESA BIOS detected

(II) fglrx(0): VESA VBE Version 3.0

(II) fglrx(0): VESA VBE Total Mem: 16384 kB

(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS

(II) fglrx(0): VESA VBE OEM Software Rev: 9.12

(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 

(II) fglrx(0): VESA VBE OEM Product: M56P    

(II) fglrx(0): VESA VBE OEM Product Rev: 01.00

(II) fglrx(0): ATI Video BIOS revision 9 or later detected


> 
(II) Loading sub module "fglrxdrm"

(II) LoadModule: "fglrxdrm"

(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so

(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."

	compiled for 7.1.0, module version = 8.34.8

	ABI class: X.Org Server Extension, version 0.3

(--) fglrx(0): VideoRAM: 262144 kByte, Type: DDR2

(II) fglrx(0): PCIE card detected

(WW) fglrx(0): board is an unknown third party board, chipset is supported


> 
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)

(EE) AIGLX: reverting to software rendering

(II) Loading local sub module "GLcore"


Thanks for your time!

---

### Post by de_RiN on 2007-03-01
Adamk in the #beryl channel on irc.freenode.org was kind enough to help me out.

After the last update starting the beryl engine from the beryl-manager doesn't work anymore. Run this "LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl --replace &" in your shell and it should work correct.

ps. Now another thing I have is missing decoration on windows, in my case, the top windowbar isnt there ( the on with minimize, restore size and close ) isn't there anymore. Sometimes its a smaller white shadow drop on top of the windows. And sometimes it are distorted small scratches of pixels where the bar should be. This seems to be a Emerald bug. But I could not find any info about it only for nVidia cards.

---

### Post by Frazer on 2007-03-03
Ill try this thanks, ill edit how I have done when I do it.

EDIT:
still no luck

I get this when I run beryl in the terminal

**************************************************************
* Beryl system compatibility check                           *
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

2nd EDIT:

It randomly started to work on my 3rd boot lol
any commands I can run to maybe help anyone else?

---

### Post by nardis_Miles1 on 2007-03-04
I have also had the white screen problem. However, there is a workaround to this. 

Instead of issuing the simple

beryl-manager

You issue the command:

beryl-manager --no-force-window-manager

and then, to start the window manager, issue

beryl-xgl --use-copy

If your white screen is for the same reason as mine, it is an acknowldged bug in beryl.

---

### Post by fsando on 2007-03-05
I followed the original guide of this thread - and it worked (edgy+beryl+xgl+x1600)
After the installation I made sure everything was working - THEN I DISABLED ALL BERYL REPOSITORIES.
Now I'm pretty confident it will work (at least till next xorg upgrade (but I think I'll pass that one over if et comes).

Big thanks happis!

---

### Post by Frazer on 2007-03-06
I did that and everything was working, disabled the beryl repos and today its just randomly stopped working lol.  On boot this morn I have no beryl.... random

---

### Post by fsando on 2007-03-09
Did you get the beryl-manager icon?
If so, did you try **Select Window Manager > Beryl**?
I've experienced that it took a couple of Beryl startups before it would start the window manager automatically. 
My guess:
Maybe beryl needs certain files to be present, If they are not, beryl will create them.
If there is some dependence between these files beryl may take a few startups before they are all created.

EDIT: You should, of course, disable the repo when your installation works ;)
It has happened a couple of times (with my present install) that Beryl has crashed when I resized a window upwards. I'l live with that till Feisty.

---

### Post by Frazer on 2007-03-09
I think it was somthing to do with my XGL sesion, I removed it and made a new one and iv had no problems the last few days :)

---

### Post by namregzepol on 2007-03-14
can any of you put a 1280x800 resolution in the ati x1600? If so, can you post how?

---

### Post by spigolo on 2007-03-14
I installed Xgl, beryl and fglrx drivers on an ati x1600 today. everything fine, except that the session with xgl messes up  all the icons and widgets (it kinda goes back to an older gtk style) and i can't seem to change theme. this is broken on xgl even with metacity as wm.
starting the session as normal default gnome gives me back the good old human feel. 
is there a way to have exactly the same buttons and widgets on xgl?

Edit: solved! i had to run gnome-settings-daemon

---

### Post by Frazer on 2007-03-15
> **namregzepol said:**
> can any of you put a 1280x800 resolution in the ati x1600? If so, can you post how?

What drivers did you use?

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

I used method 2 on there in Edgy and it just did it itself.

If all else fails you could edit your xorg.conf

add the resoloutions you want to the big list in that file

---

