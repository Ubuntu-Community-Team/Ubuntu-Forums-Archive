---
title: "AMD64 install problems"
date: 2005-08-05
forum: Desktop Environments
---

### Post by daver10 on 2005-08-05
I installed kubuntu 5.04 today, once using the 32-bit version on a P4 machine, and four times on an AMD64 box.  The 32-bit install went great.  Loved the eye candy.

The 64-bit installs have been the worst I have seen since Slackware 1.0.  Well, OK, not that bad, but the worst experience with a modern linux distro.  

I have gone through the install 4 times trying various things to get it to work, and the result is always a grey X server screen with a movable mouse cursor and no keyboard control.  The keyboard is there for the install and boot, it just goes away when the X server starts.  I have booted into single user mode a few times and started kdm, the result is the same.  Tried several PS2 keyboards that have always worked fine in Linux, no change.  

During one install the partitioner confused one hard drive with another.  I had selected the second partition on drive one to use as /boot and the third as /.  When it presented the summary screen it was asking to format the third partition on the second drive as root, which was FAT32 and had been configured to mount as /dos.  Pay attention to that warning screen, there seems to be a bug in there smewhere.

The mobo is an Abit KV8 Pro, video is Geforce 6200.  

I will work on xorg.conf as soon as apt-get update finishes.  The X server is starting though, and it appears to be in the selected resolution based on the cursor size, but there is no KDE there, just the basic X server.  

Has anyone solved the grey-screen of eternal lockup problem?  Can you share the fix?

---

### Post by Drain on 2005-08-05
I had some strange difficulties with the Kubuntu install on my AMD64. When I used the Kubuntu 64 livecd, it ran just fine, but I had strange errors when I tried to use the install cd. I switched over to regular ol' Ubuntu and Gnome, and then did an apt-get install of kubuntu-desktop, and everything works great that way. But I'm guessing that's not what you want to do... 

Anyway as I was thinking about it, I thought perhaps if when you insert the install cd, and are given the initial prompt, you type "server" for a bare-bones installation, and then "apt-get install x-window-system-core kubuntu-desktop". It would take a while to download all the packages, but then again, so would downloading another CD. 

Good luck.

---

### Post by daver10 on 2005-08-05
Checked the logs, no abnormal errors in them (just the usual font path crap)  and the xserver still starts, just without a keyboard or KDE.  I started it using the kdm command.  I tweaked xorg.conf a bit to make sure the screen was correct, didn't help, nor did I think it would.  I have a valid screen, just no desktop.

The logs all look normal, as does everything else.  Except for the grey screen and the disabled keyboard everything is fine.  The video card is detected and it finds two modes it likes, everything is going fine until it loads its generic US 104 keyboard driver.  At that point all the lights on the keyboard go out and that is the end of that. 

Since I can't switch terminals with a dead keyboard, I can't see what errors might be sitting on TTY1.  I ssh'd into the box and there is nothing interesting happening in any of the log files.  As far as the system is concerned everything is great.  

As a last gasp measure and after downloading the ubuntu install disk, I am running apt-get install kde to see if that helps or just overruns the hard drive.

Gotta love that FiOS though.  15 mbps rocks.  135 mb d/l'd in the time it takes to type half a sentence.

Ooh. it gets better.  I can't even kill -9 the stuck xserver.  Locked it up real nice, but it would not free up the terminal.  I was able to reboot it though, and the kde install did not help.  Not much left to do besides archive the etc directory and go back to Ubuntu proper.

Ubuntu 5.04 has always worked fine on this box, at least until XP x64 decided to kill it during its install.   I finally got around to reinstalling a Linux distro and this has been the result.   

Strange, the Ubuntu install looks to be running two or three times as fast as the Kubuntu install.  Other posters have mentioned AMD64 performance issues with this distro as well.  

OK, it's done.  I have a login screen, keyboard, and mouse.  The Ubuntu distro copied in about four times as much data and still installed in half the time that Kubuntu took.  Something is broken in the AMD64 install.

---

### Post by Drain on 2005-08-05
Well, freaky. On the bright side, downloading iso's for you isn't a big deal (especially with that link). But glad you got something working there.

---

