---
title: "Only 3.11.0-23 Works"
date: 2014-10-08
forum: Desktop Environments
---

### Post by rob102 on 2014-10-08
Howdy,

I'm running Ubuntu 14.04 LTS 64-bit on a ASUS AMD A8-3870 with Radeon. This is on a dual boot with Windows 7.
For some reason the 3.13.0-35, 3.13.0-32, and 3.13.0-30 versions on the boot loader don't work. By that I mean, the USB keyboard doesn't seem to be recognize and I get a black screen after the initial Ubuntu logo on boot up.

It sounds like the OS boots, since I get the log-in sound, but no screen or keyboard. If I use 3.11.0-23, everything is happy.
I have tried the 3.13.0-35 recovery mode and enabled networking. I then did a fix broken packages (I think that's what it is called). It downloads and does the fix and boots normally. When I do a full boot, it does the black screen thing again.

I'm still a bit of a noob on the OS, but I'm looking at possible alternatives to Windows. I'm hoping someone can steer me in the right direction for what to try next. Any help is appreciated.

-Rob

---

### Post by Frogs Hair on 2014-10-08
Welcome rob102

If you have the 3.11 kernel it indicates an upgrade from 13.10 . Is this a traditional dual boot or did you use the Windows installer? (Wubi) If you used Wubi there is problem that causes the file system to be read only when the new kernel is booted post upgrade. If you partitioned the drive and did a true dual boot there is a possibility of fixing the installation. The link describes Wubi. [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by rob102 on 2014-10-09
Thanks for the response Frogs Hair.
Windows was installed first. The hard drive was partitioned and Ubuntu was installed on the second partition. I booted up to the DVD drive and installed Ubuntu from DVD. I'm guessing this would negate the Wubi scenario?
I would like to keep from having to do a fresh install of Ubuntu if possible. Having said that, it is not out of the question. The Windows partition has to stay intact though.

---

### Post by Frogs Hair on 2014-10-09
If you can hear the login sound it is likely  graphics card related. Can you provide some information about your system.

---

### Post by rob102 on 2014-10-09
Motherboard ASUS F1A75-M LE A75 FM1 R.
Processor AMD A8-3870K 30.G 4M FM1 R.
The processor has embedd Radeon HD6550 graphics. There isn't another video card, using the embedded graphics.

I thought it sounded like a graphics card issue too, but the USB keyboard doesn't appear to be active either. Of course, it's hard to know for sure without a screen. The num lock LED isn't lit up as it normally does on boot up.

---

### Post by Frogs Hair on 2014-10-09
Did you upgrade with the default graphics driver installed or were you using a driver from additional drivers ?

---

### Post by rob102 on 2014-10-09
I'm pretty sure I was using the default driver because I had some major issues when I tried using one from ATI/AMD. I can't swear that I wasn't, but I'm 80% sure I was using the default.
Should I try a proprietary driver?
Is there a way to reinstall the default driver?

---

### Post by Frogs Hair on 2014-10-09
Yes, you can install the default driver  from your working session. It's easy to locate packages in the synaptic package manager and then right click and mark for re-installation .```
 sudo apt-get install synaptic
```

---

### Post by rob102 on 2014-10-10
Well I had to install the Synaptic package manager. It wasn't in my apps.
I dig some digging and found drivers specific to the ATI/AMD Radeon and installed the package (fglrx-updates). I've booted a couple of times now and it appears to be working again. :p
Thanks again for the help and steering me in the right direction.

Next on the agenda is to figure out how to enable serial port operation by default. I keep getting access denied cannot open /dev/ttyS0: Permission denied. I'll get to it after I get some work done.

---

### Post by rob102 on 2014-10-20
I tried using the proprietary driver listed for fglrx-updates. I remember why I had to stop using the propietary driver in the first place - unexplained lock-up. The screen just freezes and I can't do anything. No cursor movement or anything.

I am now trying the proprietary drive for fglrx for AMD. I waiting to see how it behaves. I would like to use the default/tested one, but when I tried, it went back to the original problem - blank screen.

---

