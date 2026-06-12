---
title: "Ubuntu 9.10 on Inspiron 1100 with 845G Video Card"
date: 2009-11-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Drycola on 2009-11-01
Hi, I have a DELL Inspiron 1100 laptop with Intel 845G Graphic Card running Ubuntu 7.10 smoothly with a lot of desktop effect, unfortunately, 7.10 is no more supported and I need to get a newer supported release.
I brought the newest 9.10 a few days ago, and ran it on LiveCD, but when I go to enable Desktop Effects I get a message telling me that it could not be enabled. I think this problem is similar to the problem in 9.04 but I've heard that it has been fixed.
So, how can I enable Compiz Effects on Ubuntu 9.10 with Intel 845G Video card???

---

### Post by Turtle.net on 2009-11-01
Try [this]("http://ubuntuforums.org/showpost.php?p=8209826&postcount=2")

In the future please search the forum first. Thanks :D

---

### Post by TheDigitalEagle on 2009-11-01
This does not address or fix the issue in the original question.

The driver is correctly found and used in 9.10, as well as the chipset is found and recognized as being in OpenGL mode and not software mode. So really, everything lines up where 845G chipsets SEEM like it should work, however the graphics are still slow and desktop effects are not available. Uninstalling and reinstalling already the correct drivers isn't the case, it's also not the case that Ubuntu things its a Radeon.

Example:
```
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 845G GEM 20090712 2009Q2 RC3 x86/MMX/SSE2
 
```

Another Example: 
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

```

I would say, don't accuse someone of not trying to do some research. I myself have been researching this issue ever since 9.10's release with no light to the issue.
They, like I, have probably been trying to track down a solution for a while. Please don't accuse someone of not trying. :)

---

### Post by Turtle.net on 2009-11-02
Excuse me if I "accused" without knowing. But you see, I have an Intel card 945GM that works perfectly fine with driver intel (default installation).
So I guess that having compiz working with an intel card should not be that difficult.

Again my deepest apologies if I hurt anyone's feeling.

---

### Post by jposs526 on 2009-11-02
Desktop effects can be used with the 845G?

I'm using a Dell Dimension 2350 desktop (about 7 years old) with a 1.8GHz Celeron (socket 478), 1GB PC2100 and the very same integrated graphics. I didn't think it was possible to use desktop effects with the 845G.

I'm not completely new to Linux, I've tried kubuntu 8.04 but no luck (maybe burned a bad image though, so no particular blame). Then tried ubuntu 8.10 and had everything going very well, except no desktop effects. Same when I switched up to ubuntu 9.04 and now I'm on ubuntu 9.10 and still no desktop effects. Matter of fact, I'm now stuck with 800x600 res even though I've always used 1024x768 and higher in 9.04 and even in Mint and OpenSuSE.

Seems there is something going on with xorg.conf where manual setup is required. Possibly have to create an xorg.conf file to get everything going?
Have you checked out your xorg.conf file? I opened mine up in gedit and found it was a blank file. Only been a problem in 9.10 though, so possibly a bug.

---

### Post by bolweval on 2009-11-02
> **TheDigitalEagle said:**
> I would say, don't accuse someone of not trying to do some research. I myself have been researching this issue ever since 9.10's release with no light to the issue.
They, like I, have probably been trying to track down a solution for a while. Please don't accuse someone of not trying. :)

I feel for ya man, I gave up asking anyone here for help, same thing every time. I think its a big reason for Linux being so slow to adopt, everyone treats you like a dumb sh_t every time you ask a question. :(

---

### Post by grege on 2009-11-10
I just dug out my old Inspiron 1100 and installed Karmic.

I am beginning to think compiz may be impossible. Up until Jaunty you could use the i810 driver to at least get 2d and xv. The i810 driver is no longer provided. The new versions of the intel driver only support UXA acceleration and mine will load the driver, but it does not provide any acceleration.

It may be possible to install the i810 from jaunty to at least get 2d.

I am still working on it.

ps

Kubuntu has not worked since the move to KDE 4.

---

### Post by grege on 2009-11-10
To get 2d and video acceleration follow these instructions.

[http://www.ubuntu.com/getubuntu/releasenotes/910#No%20Xv%20support%20for%20Intel%2082852/855GM%20video%20chips%20with%20KMS](http://www.ubuntu.com/getubuntu/releasenotes/910#No%20Xv%20support%20for%20Intel%2082852/855GM%20video%20chips%20with%20KMS)

I also edited /etc/default/grub to remove splash screen on boot.

Seems to be good 2d now. 3d may be impossible, the chipset is old and flakey.

---

### Post by grege on 2009-11-10
One last post for Inspiron 1100 users. As well as the turning off of KMS, by adding mesa-glx and using the below xorg.conf I can make glxgears run at about 300fps. Extreme Tuxracer will run, but it is jerky. If you override the blacklist and try and load Compiz the system freezes. So good 2d is achievable, 3d is useless. I still get occasional black screens (when playing with 3d stuff mainly) requiring a power down, but that has always been the bane of Linux on a Dell Inspiron 1100. If you stick to a 2d desktop and non-3d programs it should run Karmic reliably. Xv video accel works well.

xorg.conf

Section "Module"
Load       "dri"
Load       "glx"
EndSection

Section "Device"
Identifier "Intel 82845G/GL"
Driver "intel"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Internal monitor"
Option "DPMS"
HorizSync 28-80
VertRefresh 43-60
EndSection

Section "Monitor"
Identifier "External Monitor"
Option "DPMS"
HorizSync 28-80
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel 82845G/GL"
Monitor "Internal monitor"
DefaultDepth 24
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection

Section "DRI"
    Mode 0666
EndSection


If anyone achieves a better result on an 1100 please share your config.

---

### Post by yknivag on 2009-11-10
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) worked for me on Jaunty (9.04).  Unfortunately no-one can tell me whether it will work on 9.10.

Until someone can confirm then you may be better using the last LTS release (8.04 - Hardy Heron).

---

### Post by ronmon on 2009-11-11
@grege Thanks for the xorg.conf. I had already installed the testing kernel and put the nomodeset option in GRUB and those things helped some. But the xorg.conf really helped smooth it out. This is an old laptop that somebody gave me with a dead HDD, so for the price of a cheap drive from newegg I have a fairly decent machine. Maybe I'll invest in some more RAM (only has 256MB), but with 1GB of swap it runs okay for now.

Anyone who expects an old piece like this to give you all the flashy stuff is not being realistic. I'm using xubuntu without compiz.

---

### Post by XyzzyZork on 2009-11-15
> **ronmon said:**
> Anyone who expects an old piece like this to give you all the flashy stuff is not being realistic.

I'd have to disagree from experience...  My laptop is 1.6GHz, Intel 855GM video, and in each release from Hardy to part-way through Karmic beta, Compiz worked fine in GNOME without monopolizing resources. 8) 

I came here through a forum search for Intel-Compiz conflicts in Karmic. There's a *lot* of people with Intel video cards running into the same issue on laptops from all kinds of manufacturers. (In my case, it's an Averatec.)

---

### Post by grege on 2009-11-17
> **XyzzyZork said:**
> I'd have to disagree from experience...  My laptop is 1.6GHz, Intel 855GM video, and in each release from Hardy to part-way through Karmic beta, Compiz worked fine in GNOME without monopolizing resources. 8) 

I came here through a forum search for Intel-Compiz conflicts in Karmic. There's a *lot* of people with Intel video cards running into the same issue on laptops from all kinds of manufacturers. (In my case, it's an Averatec.)

The Dell Inspiron 1100 series are a special breed that have always been difficult with GNU/Linux due to the way Dell configured the shared video memory.

---

### Post by dirk_k on 2009-12-03
Installing kernel 2.6.32 (from [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")) seems to solve it partially: glxgears went from 75 to 230 fps (remember to remove xorg.conf if you created it before). But I still have other problems with the laptop (using the netbook remix):
- Black screen half of the time: seems to be something with the intel driver selecting VGA output instead of the LVDS that drives the laptop monitor.
- Netbook remix launcher will crash X/intel driver.
- Wifi problem with hostap driver.

---

### Post by swiftarrow on 2010-02-06
> **yknivag said:**
> [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4) worked for me on Jaunty (9.04).  Unfortunately no-one can tell me whether it will work on 9.10.


I've done this on my Inspiron 1100, intel 845G graphics card, in Karmic (ubuntu 9.10).

I tried replacing jaunty with karmic in the instructions given on that link, but apt-get was unable to find the 2.4 driver.  

Finally I downloaded the package from [http://ppa.launchpad.net/siretart/ppa/ubuntu/pool/main/x/xserver-xorg-video-intel-2.4/](http://ppa.launchpad.net/siretart/ppa/ubuntu/pool/main/x/xserver-xorg-video-intel-2.4/)  (apt-get takes it from the same place; choose the right one for your architecture) and installed it using dpkg (double-clicking on the downloaded file).

Doing this stopped my inspiron 1100 from freezing every so often.  Unfortunately, the problems that came with 8.04 (occasional black screens on boot) returned, but that is ok.  As long as it doesn't keep freezing over.

> To get 2d and video acceleration follow these instructions.

[http://www.ubuntu.com/getubuntu/releasenotes/910#No%20Xv%20support%20for%20Intel%2082852/855GM%20video%20chips%20with%20KMS](http://www.ubuntu.com/getubuntu/releasenotes/910#No%20Xv%20support%20for%20Intel%2082852/855GM%20video%20chips%20with%20KMS)


I did follow those instructions, but it's too early to tell if it made a difference with anything.

The only problem is that I can't get compiz to work, yet.  I absolutely need compiz for the negative effect - that is a real eye-saver.

Having done these two things, running compiz-check from [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check) reports a warning that my chipset may be blacklisted in some distributions.

running compiz --replace shows that it certainly is blacklisted.

Disabling blacklist checks allows 'compiz --replace' to start up, but then X is restarted, and compiz is not running.

I ran 'compiz --replace >> log' and here's the output from the log:

> Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2562' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Starting gtk-window-decorator

At this point, X is restarted, and I*have to log in again.  Compiz is not running.
How can I get compiz to run instead of restarting X?

---

### Post by shadetree1 on 2010-02-06
Take a look here:  [https://bugs.launchpad.net/bugs/456902](https://bugs.launchpad.net/bugs/456902)  PPA ;)

---

### Post by Zerp64 on 2010-02-16
Are you... are you sure about this? I mean, I'm running 9.10 and with a few tweaks I've got my glx running at about 1200-1300 fps.

> **grege said:**
> One last post for Inspiron 1100 users. As well as the turning off of KMS, by adding mesa-glx and using the below xorg.conf I can make glxgears run at about 300fps. Extreme Tuxracer will run, but it is jerky. If you override the blacklist and try and load Compiz the system freezes. So good 2d is achievable, 3d is useless. I still get occasional black screens (when playing with 3d stuff mainly) requiring a power down, but that has always been the bane of Linux on a Dell Inspiron 1100. If you stick to a 2d desktop and non-3d programs it should run Karmic reliably. Xv video accel works well.

xorg.conf

Section "Module"
Load       "dri"
Load       "glx"
EndSection

Section "Device"
Identifier "Intel 82845G/GL"
Driver "intel"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Internal monitor"
Option "DPMS"
HorizSync 28-80
VertRefresh 43-60
EndSection

Section "Monitor"
Identifier "External Monitor"
Option "DPMS"
HorizSync 28-80
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel 82845G/GL"
Monitor "Internal monitor"
DefaultDepth 24
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection

Section "DRI"
    Mode 0666
EndSection


If anyone achieves a better result on an 1100 please share your config.

---

### Post by shadetree1 on 2010-02-16
Yea, the PPA is running almost 2K?

---

