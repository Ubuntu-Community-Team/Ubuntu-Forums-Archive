---
title: "3D problems with radon xpress 200"
date: 2006-06-16
forum: Desktop Environments
---

### Post by Steven_B on 2006-06-16
I have a radeon Xpress 200.  When using the newest xorg-driver-fglrx (7.0.0-8.25.18+2.6.15.11-1),  X crashes when I try to log out.  Switching to the "ati" driver or downgrading makes the problem go away: 
[http://www.ubuntuforums.org/showthread.php?t=185163](http://www.ubuntuforums.org/showthread.php?t=185163)
As a result, I am using the 8.24.8-1 driver.  However, I am unable to get hardware 3D acceleration.  Xorg.0.log shows:
```
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0xb720b000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```
Is there a way to downgrade just my kernel module, or do I have to downgrade my whole kernel?  In either case, how do I do that?  Is there another way around this problem?
Thanks!

---

### Post by InDenial on 2006-06-16
I do not have any problems running 3d with my Ati Radeon Xpress 200M. Did you follow the ATI driver install howto?
[URL="http://www.ubuntuforums.org/showthread.php?t=24557&pp=10"]
ATI HOWTO[/URL]

---

### Post by zapcojake on 2006-06-16
I have a radeon xpress200 also and mine works just fine.  I used the fglrx I found in synaptic.  I also sucessfully installed it with Ati's driver package on Kororaa on this same computer.

---

### Post by mochaspro on 2006-06-16
Can you guys explain how did you get your 3D with xpress 200M working? it's driving me crazy :-( 

If i install the 8.24 drivers form ATI (making the .debs or just running it), then compiling them with /lib/modules/fglrx/ OR just instally the packages that comes with the synaptic and doing fglrxinfo i get not mesa drivers (wich is good) BUT my  Gdm loads up fine, but as it loads to the desktop, the gdm screen remains in the background, then all my stuff looks weird and 99% of time it freezes... 

Can someone with the same problem help me please?

---

### Post by InDenial on 2006-06-16
2 posts back I gave a link to a topic which worked for me.:
[**[COLOR="Red"]LINK[/COLOR]**]("http://www.ubuntuforums.org/showthread.php?t=24557&pp=10")

---

### Post by onlybui on 2006-06-16
Do you have any problems with running mplayer full screen?...

---

### Post by Steven_B on 2006-06-17
I can get 3D with the latest version of the xorg-driver-fglrx from the repositories.
However, it crashes when I try to log out or shut down the computer.  What versions of the fglrx drivers are you using?  Are you using gdm, and if so, what version?
Thanks!

---

### Post by InDenial on 2006-06-17
I have all the latest drivers from the reps. I do not have any problems with my laptop crashing. I used the link I gave and that's it. 

I saw however somewhere a bug report about more people having these problems. 

[Lockup problems with both the free xorg ATI driver and the proprietary fglrx driver, using various ATI cards]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30447")

---

### Post by InDenial on 2006-06-17
[QUOTE=onlybui]Do you have any problems with running mplayer full screen?...[/QUOTE]

Not sure if this post was directed to me, but.. at the moment I have no mplayer running. Will test it later when I am ready setting up my laptop.

edit: tested is and mplayer runs in full screen here no problems.

---

### Post by Steven_B on 2006-06-29
Has anyone been able to get the old driver (8.24.8-1) working in dapper?  Or, is there a way around the logout/shutdown crashes?

---

### Post by Steven_B on 2006-07-07
I've upgraded to the newest driver - 8.26, and it works great!

---

