---
title: "unable to enumerate usb device"
date: 2009-01-15
forum: General Help
---

### Post by Doug77 on 2009-01-15
I decided to turn off the splashscreen so I could see what Ubuntu was doing when it loaded, and I noticed that it give this error message early on in the boot:

unable to enumerate usb device

It boots up fine and works fine, but I'm wondering what that means and if I should do anything about it.  I'm running Intrepid (fresh install, not upgraded), x86.  

Thanks!

---

### Post by iaculallad on 2009-01-15
To find out more information on that message, issue the command below on your terminal:

```
dmesg | tail
```

---

### Post by Doug77 on 2009-01-15
Hmm, it gives me a bunch of messages like this: 

[   89.089131] [UFW BLOCK INPUT]: IN=ppp0 OUT= MAC= SRC=116.4.184.64 DST=59.104.34.199 LEN=48 TOS=0x00 PREC=0x00 TTL=106 ID=15933 DF PROTO=TCP SPT=3770 DPT=19235 WINDOW=16384 RES=0x00 SYN URGP=0 

And that's all.. any ideas?  I noticed that sometimes the "unable to enumerate usb device" doesn't appear on boot, and sometimes it does.  On the time I ran dmesg, it appeared on boot.

---

### Post by john183 on 2009-01-15
I get that same message when i boot while my Misrosoft USB trackball is plugged in, but it doesn't come up if the trackball is unplugged. I just figure that it has to do with the fact the Xserver isn't running yet so the OS doesn't really know what to do with the mouse-type input device. I wonder if that is the same thing that is happenoing to you.

---

### Post by KeyserSoze93 on 2009-01-15
If it doesn't cause any problems, it's probably nothing to worry about. You can make sure all the USB devices are seen, by running ```
lsusb
``` in the terminal.

If your BIOS has an option to "Disable Legacy USB Support", you could try enabling that, it means the BIOS won't interfere with the USB drivers and will leave it up to the operating system, which is fine for Linux.

This solved some USB related issues I had with several Debian machines.

---

### Post by Doug77 on 2009-01-19
Okay thanks for the information!  

Since everything is working fine, I don't think I'll experiment with the bios.  Just wondering what that message meant.

---

