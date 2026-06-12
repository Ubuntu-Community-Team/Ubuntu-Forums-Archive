---
title: "Webcam not working on inspiron after upgrade from 8.04 to 9.04"
date: 2009-10-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nomenclature3000 on 2009-10-23
Hi, I have an Inspiron 1420 that was, until this morning, running Ubuntu 8.04. I upgraded to 8.10 and then 9.04 and everything seems okay except that my webcam isn't working at all. I've been browsing around the forums for the last hour for an answer, but I'm having a hard time solving this. 

When I run camorama I get "Could not connect to video device (/dev/video0).".

Here is the output of lsusb:

```
adam@tinkerbell:~$ lsusb
Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Any help or suggestions are sincerely appreciated!

Thank you,
Adam

---

### Post by nomenclature3000 on 2009-10-23
A few more data points:

```
adam@tinkerbell:~$ ls /dev | grep video
adam@tinkerbell:~$ mplayer /dev/video
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video.
File not found: '/dev/video'
Failed to open /dev/video.


Exiting... (End of file)
```

---

### Post by Dangger on 2009-10-25
Were you able to solve this?

---

### Post by nomenclature3000 on 2009-10-25
I wouldn't say I "solved" it, but the webcam is now working. I'm not sure what I did -- maybe it was just rebooting.

Since the upgrade, I still can't have both skype and other sources of sound (e.g. Rhythmbox or Flash Player) open simultaneously: skype reports "problem with audio playback" if it's opened second. If other sources of sound are opened second, they simply refuse to play. But this is a separate issue.

---

### Post by erick_king on 2009-10-25
I have a dell mini10 and it works fine with Fotmaton Cheese

---

### Post by Dangger on 2009-10-25
> **nomenclature3000 said:**
> I wouldn't say I "solved" it, but the webcam is now working. I'm not sure what I did -- maybe it was just rebooting.

Since the upgrade, I still can't have both skype and other sources of sound (e.g. Rhythmbox or Flash Player) open simultaneously: skype reports "problem with audio playback" if it's opened second. If other sources of sound are opened second, they simply refuse to play. But this is a separate issue.


Ok, I can't believe that installing Cheese and rebooting fixed it for me. I actually don't even know if it was only rebooting. If you have gone through the trouble of upgrading to 9.04 I strongly suggest trying 9.10, intel video works 100% better and flash is excellent. I have no trouble using skype video call with rythimbox open.

---

### Post by aperomsik on 2009-11-11
>  I can't believe that installing Cheese and rebooting fixed it for me. 

Well, it worked for me too, so thanks for mentioning it.

---

### Post by avacado on 2009-11-22
Linux strider 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

DELL inspiron 1520
intel core 2 duo 2.4GHz 
omnivision webcam

webcam works fine when cheese loaded, thanks

---

