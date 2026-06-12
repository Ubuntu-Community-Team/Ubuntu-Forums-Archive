---
title: "Blank screen on startup every time"
date: 2008-05-02
forum: Desktop Environments
---

### Post by nosegoblin on 2008-05-02
I've recently started having this annoying problem first with 7.10 and now after upgrade also with 8.04 lts. I don't remember doing any changes to the system when this started. 

The problem is that when I'm booting up the PC the GUI will never show up. They way I have bypassed this so far is to change to terminal (ctrl+alt+F2), login, delete the /tmp/.X0-lock file and reboot the computer. Now the GUI/Gnome is working like it should be until I shutdown/reboot the computer and then the problem is there again. 

I've tried to google some answers to this but I can't seem to find a working one so I'm relying on all of you to help me with this one. Please help me to even find a place to start with.

---

### Post by Royke on 2008-05-02
Hello there, i'm had the same problem and i rebooted into recovery mode and then restarted x. I'm trying now with EnvyNG to fix the driver-ploblem so the desktop-effects can be used again. If it worked i will see now, have to restart...

---

### Post by Royke on 2008-05-02
...no success. it WILL work, don't worry!

---

### Post by Zorael on 2008-05-02
After changing to that Alt+F2 terminal, make a copy of **/var/log/Xorg.0.log** (to, say, /tmp or your home directory), then dissect it/post it here. There's likely some critical error noted near the end.

To reset your X configuration, if you haven't tried that already, reconfigure xserver-xorg.
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup0805
$ sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Royke on 2008-05-02
I think all people with distorted/blank screen-problems should read this: [http://ubuntu-tutorials.com/2006/12/13/kernel-update-affects-some-nvidia-users-fix-included/]("http://ubuntu-tutorials.com/2006/12/13/kernel-update-affects-some-nvidia-users-fix-included/")
:guitar:

---

### Post by jazmin123 on 2008-05-02
Hi folks,
it is the same problem by me. I have found one solution but i am in hurry (friday afternoon :)) ...

here is what you have done and what plus should do >>> 
ctrl+alt+f2
remove X0-lock
startX
go to Login Window -> enable Automatic Login !!!!!

i have made it and 3. day i log automatically ... without problem.

To be honest, someone should take care of that problem and find the real reason ... it is not about nvidia, i do not have one.

Btw. my system crashed a week ago. so i waited and run brand new install of 7.10 and immediately 8.04 and it happened to me!!!

In Ubuntu forum i have recently seen lots of (tones ;)!!) of people describing the same issue always with some other words. Mark my word ;)!

C U 

Jazmin123

---

### Post by nosegoblin on 2008-05-03
The weirdest thing happened today as the problem suddenly dissappeared and once again I had not done anything special about it. Just read some e-emails and browsed the web. 

I hope that the situation will stay like this. :) Thanks for your help anyways.

---

### Post by nosegoblin on 2008-05-03
I Should not have been so hasty with my previous message as the issue appeared again after couple of boot rounds when verifying that the problem really has disappeared. 

I already have the automatic login enabled as I'm the only user of this computer and also I have ATI radeon 9600pro graphics adapter so at least this is not any Nvidia issue. 

As the Xorg.0.log file is quite big, I'll post only the errors/warnings below:
```

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.

(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success

(II) Primary Device is: PCI 01:00:0
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset ATI Radeon 9600 AP (AGP) found

(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 3
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xe7ffe000 is: 0xe7ffe000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xf87ff8

(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 3
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 16
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xe7ffe000 is: 0xe7ffe000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xf87ff8


```

---

### Post by jazmin1234 on 2008-05-05
Hi "nosegoblin",

here i must admit that my knowledge or experiences of linux/ubuntu go not so far as reading a log and presuming some actions based on log, unfortunately because i'd like to help.

i can image what kind of pain it can be to set up ubuntu to work for you. On the other hand, you would teach yourself a lot these days ...

Ok, only advice I can give you is to try login and repeat what I have posted on friday. If ubuntu works fine, and you can read emails, browse etc. ... it is ok!

... if not, you have to wait for someone to look at this discussion and come with some "more professional" help.

Jazmin1234

p.s. still seeing new posts with similar issue, but no general solution :(

---

### Post by nosegoblin on 2008-05-11
Still having these issues. I'm just wondering that is there a way to execute the "sudo rm /tmp/.X0-lock" automatically in the shutdown? What I mean is that the file would be deleted automatically when I'm shutting down the computer and thus bypass this startup problem. I know this is not a very elegant way to fix the problem but it would be least a good start. 

I have also found out that there seems to be the same problem when the computer enters powersaving mode. I'm unable to resume back to the GUI after this.

---

### Post by pickarooney on 2008-08-02
I have this same problem (Kubuntu 8.04 on a laptop) and the tutorial fails to resolve the problem as apt-get can't remove linux-ubuntu-modules because it can't find it.

Basically my laptop's hardware is incompatible with Hardy, which is quite the pain in the ****.

---

