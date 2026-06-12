---
title: "sound works from terminal, but not from menus"
date: 2005-08-14
forum: Desktop Environments
---

### Post by wactuary on 2005-08-14
I've been looking around a solution to this problem but I'm stumped.

I've installed gcompris for my kids.  When run from the Applications->Games->Educational suite gcompris, I get no sound.

When I run the command "gcompris" from a terminal, I get sound.

I am guessing the problem is from an environment variable, but I don't see any that should make a difference.  The user is in the audio group and the permissions seem OK.

```
/dev$ ls -l |grep audio
crw-rw----  1 root audio    14,  12 2005-08-14 10:50 adsp
crw-rw----  1 root audio    14,   4 2005-08-14 10:50 audio
crw-rw----  1 root audio    14,   3 2005-08-14 10:50 dsp
crw-rw----  1 root audio    14,   0 2005-08-14 10:50 mixer
crw-rw-r--  1 root audio    10, 135 2005-08-14 10:50 rtc
``` 

I get the same problem with TuxPaint.  No sound from menus, Sound from terminal command called with no options.

Can someone point me in the right direction to debug this?

(Base Hoary 5.04 installation, Alsa installed as per the Unofficial Starter Guide sound configuration instructions.)

Thanks,
Chris

[COLOR=DarkSlateBlue]
It appears that TuxPaint and gCompris are both older applications that are trying to use OSS.  I know that gCompris is using the "SDL", I'm not sure about TuxPaint.

My solution was one or both (I did them at the same time) of installing "alsa-oss" and "libsdl1.2debian-alsa".  Neither was a stock Ubuntu package, but were in Universe/Multiverse.  Both seem like a good idea.  Alsa-OSS is an abstraction layer that tricks older programs into using ALSA and therefore play nice in the sandbox.  libsdl1.2debian-alsa replaces the normally installed version which tried to use the older OSS service.  I'm surprised to see the -OSS version is part of base Ubuntu even though Ubuntu is moving away from OSS.  There must be a downside to the ALSA version and if I find out what, I will report back.

In the meantime, my kids are much happier, and therefore I am too!   :) 

[/COLOR]

---

### Post by personman on 2006-01-28
I had the same problem in Edubuntu 5.10.  I installed both of those packages.  The first one didn't change anything, but after installing libsdl1.2debian-alsa I had sound after running tuxpaint and gcompris from the menu.  But now the sound seems sluggish.  The effects in Tuxpaint are almost a second later than they should be.  I think it was fine before (when I had sound after starting the program from the terminal).

---

### Post by personman on 2006-01-28
I uninstalled that package, since the delay was so bad.  Now I'm back to where I started.

---

### Post by wactuary on 2006-01-29
[QUOTE=personman]I uninstalled that package, since the delay was so bad.  Now I'm back to where I started.[/QUOTE]
I'm not getting that delay.  I wonder if there is a configuration difference that is different.  Here is my /etc/esound/esd.conf.  I know I changed something on this around the same time.

```
[esd]
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=-as 5

```

Also, from System - Preferences - Multimedia System Selector

Under Audio tab, Default Sink - Output select the Enlightenment Sound Daemon instead of ALSA or OSS.  I don't remember if that was default or not.

My 4 and 2.5 year olds love these programs.  I hope you get it working for yours.

Chris

---

### Post by personman on 2006-01-29
I reinstalled the package and made sure my settings matched yours, but I still get the lag.  Maybe it's a hardware issue.  I just added 'pkill esd' to my gnome startup apps.  Might be a kluge, but it works fine for me.

---

