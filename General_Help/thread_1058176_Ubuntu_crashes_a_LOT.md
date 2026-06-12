---
title: "Ubuntu crashes a LOT"
date: 2009-02-02
forum: General Help
---

### Post by KyferEz on 2009-02-02
Here's the PC: 
It's a Dell GX280 with Ubuntu 8.0.4. It's got all the updates. It has an ATI video card and I'm using the ATI proprietary driver. 

It has 2gb of DDR2 ram. The ram is fine, I've done memory tests on it extensively and it always passes. I have 5 USB external drives running on it, and all are NTFS. I have the latest NTFS-3g as of about a month or two ago.

So why all the crashing? When it crashes it just freezes completely and I can't alt-1 to a terminal. I haven't tried the ctrl-alt-bksp or alt-sysrq-k or alt-sysrq-R-E-I-S-U-B because I just found out about them...

But how can I figure out what's going on?

Thanks!

---

### Post by spiderbatdad on 2009-02-02
maybe some clue in the kernel diagnostic message.
```
dmesg > ~/Desktop/dmesg.txt
```you can create an archive of that file by right click..."create an archive." You can upload the archive here, if you like, with the manage attachment tool below.

---

### Post by Crafty Kisses on 2009-02-02
As suggested by spiderbatdad, post that log, and if I were you I'd check your RAM, maybe swap it out and change it with another stick or something.

---

### Post by KyferEz on 2009-02-02
That file has lots of networking data transfer stuff in it. I'm running ktorrent and it crashes some, but I wouldn't expect that to cause the desktop to crash too...

Codename: did you read where I said I've done extensive ram tests? I've used several mem testers and all report Ok.

---

### Post by KyferEz on 2009-02-03
No one has any ideas?

---

### Post by linuxvacuum on 2009-02-03
The only time Ubuntu crashed was because of a defective memory stick I had. Software never causes Ubuntu to crash. At worst, you have to restart your GUI :)

---

### Post by jimv on 2009-02-03
8.04 locked up all the time on me too.  8.10 does not.  I suggest an upgrade.

>The only time Ubuntu crashed was because of a defective memory stick I had. Software never causes Ubuntu to crash. At worst, you have to restart your GUI

Software can cause Ubuntu to lock up, especially if that software is the kernel, and there happen to be bugs in the aforementioned kernel.

---

### Post by spiderbatdad on 2009-02-04
Sorry to be so slow getting back. That file wasn't much help. Please reboot and run the command immediately after booting. I can't really tell what is going on in that file...some type of negotiation...like your nic is tracking tcp activity, but it has filled the whole log, and may be at the heart of the problem, so we can't see what happens during boot.

---

### Post by KyferEz on 2009-02-05
Ok, here's one from a fresh reboot.

Thanks!

---

### Post by KyferEz on 2009-02-05
Just had a kernel fault. Here's the dump from after the reboot. 

Note: I do have kerneloops installed but don't know how to use it.

---

### Post by spiderbatdad on 2009-02-05
It looks crazy. Not sure what is going on. Do you have a wirless card installed but using a pcmcia card instead?
Anyway I think you should try booting with the kernel options: "pci=routeirq no_fwh_detect" see this post on how to edit the file so I don't have to type it all over again. [http://ubuntuforums.org/showthread.php?t=1057465](http://ubuntuforums.org/showthread.php?t=1057465)  post #10
good luck.

---

### Post by KyferEz on 2009-02-06
I'd prefer not to mess with the networking stuff, unless it won't mess these things up:
I've got Peerguardian and Guarddog setup right which wasn't easy for me

Thanks!

---

### Post by KyferEz on 2009-02-11
I do not have a wireless or pcmcia card installed. This is not a laptop, it's a desktop with a built-in nic.

I'll try the boot option if you can confirm that it won't affect my guraddog or peerguardian settings.

Thanks!

---

