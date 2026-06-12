---
title: "Hardy defaulting to failsafe graphics mode"
date: 2009-02-18
forum: General Help
---

### Post by stoneage on 2009-02-18
I started it up this afternoon and it won't run in anything but failsafe.
800 x 600 max resolution.
The only change is an upgrade for sudo this morning.
I tried loading my backup xorg.conf and CTRL+ALT+BACKSPACE seemed to fix it, but when I restarted to check, it went back to failsafe and now nothing will fix it. 

Can anyone help ?

I'm getting this on running nvidia-xconfig:-
> Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Undefined Device "Configured Video Device" referenced by
                  Screen "Default Screen".


ok, it seems to be a problem with the graphics driver.
I load the backup xorg.conf it looks better but the video driver is not in use (The driver is apparently in use but not enabled.), resolution claims to be 1280 x 768 (should be 1440 x 900) and refresh rate is 60 instead of 75(flickering text). If I enable the driver and restart it defaults to failsafe. 

Anyone know what is going on ?  Could it be failing to detect the card ?

(I can't use any opengl software here so Blender won't run and without it this thing is just junk.)

dmesg suggests the card is being detected:-
> 00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GS (rev a2)
02:01.0 Multimedia audio controller: Creative Labs SB Audigy LS
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

I tried reinstalling the graphics drivers, but I'm still getting nowhere.

Help ?


I tried an earlier version of the kernel, I tried force installing an earlier version of the driver (nvidia-glx-new) - still the same. It seems not to want to use a driver at all.

I would really appreciate some assistance with this.

---

### Post by stoneage on 2009-02-22
I solved this by updating to Intrepid and rewriting the xorg.conf

[http://ubuntuforums.org/showthread.php?t=1074838](http://ubuntuforums.org/showthread.php?t=1074838)
[http://blenderartists.org/forum/showthread.php?t=148775](http://blenderartists.org/forum/showthread.php?t=148775)

---

