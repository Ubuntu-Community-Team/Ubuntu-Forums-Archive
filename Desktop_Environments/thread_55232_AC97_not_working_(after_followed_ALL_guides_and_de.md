---
title: "AC97 not working (after followed ALL guides and destroying the system)"
date: 2005-08-08
forum: Desktop Environments
---

### Post by h400l3 on 2005-08-08
First time i installed ubuntu hoary the sound worked well, so i tried to play a dvd on mplayer and it just hang. So i tried to follow the all the guides i could find and did stupied things like reinstalling alsabase. I'M a NEWBIE! So i'm sorry for doing all stupied things i did. But i even cant remember all things i did. After some 'things' the sound get noisy through esd but sounds good trough alsa. I couldnt make gnome use alsa so i did some other things and now i dont have any sound modules installed.

My lspci -v
```
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Asustek Computer, Inc.: Unknown device 812a
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at e800 [size=256]
        I/O ports at ee80 [size=64]
        Memory at febff800 (32-bit, non-prefetchable) [size=512]
        Memory at febff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
``` 

lsmod | grep snd 
is empty!

what can i do??? I dont wanna reinstall all system!

---

