---
title: "Restoring A Minimised Window Is Slow / Switching To Full Screen Video is Slow Too"
date: 2009-04-27
forum: Desktop Environments
---

### Post by INTERPEGASUS on 2009-04-27
I have an ATI mobility Radeon 3400 in Ubuntu Jaunty 9.04 and I have noticed that enabling the ATI driver degrades performance on the following cases:

1-> When restoring a minimized window.
2-> When switching video to full screen.

Without the ATI driver restoring a window takes less than a second. Switching to full screen video is also very fast.

But with the ATI hardware driver it can take 2-3 seconds to restore a minimised window and 4-5 seconds to switch to full screen video using VLC.

I also have compiz enabled. 

I would like to know what is causing this issue and how to fix it?
thanks in advance!

---

### Post by s3lekta on 2009-05-01
> **INTERPEGASUS said:**
> I have an ATI mobility Radeon 3400 in Ubuntu Jaunty 9.04 and I have noticed that enabling the ATI driver degrades performance on the following cases:

1-> When restoring a minimized window.
2-> When switching video to full screen.

Without the ATI driver restoring a window takes less than a second. Switching to full screen video is also very fast.

But with the ATI hardware driver it can take 2-3 seconds to restore a minimised window and 4-5 seconds to switch to full screen video using VLC.

I also have compiz enabled. 

I would like to know what is causing this issue and how to fix it?
thanks in advance!

bump?

---

### Post by xfile087 on 2009-08-29
I've got a similar problem. Minimizing is fine but with fglrx and compiz enabled making any video fullscreen takes over 5 seconds and the video is slow and jerky. I've tried everything including trying OpenSUSE but still the same.

Running Ubuntu 9.04 fully updated with fglrx drivers installed via jockey.
Running on an M4A78 Pro mobo with 8GB ram, ATI HD4670 GPU and AMD Dual Core 7750 CPU at 3ghz.

I just don't get it...

---

### Post by sbsbessa on 2010-02-23
Same here with an HP EliteBook 6930p running Ubuntu 9.10 64bits and I have also tried 32bits before...

Main specs are as follows.

CPU: Intel Intel(R) Core(TM)2 Duo CPU     T9550  @ 2.66GHz
RAM: 4 GB 800 MHz DDR2 SDRAM
HDD: 250 GB 7200 rpm SATA II
GPU: ATI Mobility Radeon HD 3400 Series with 256Mb DDR3 700Mhz

As anyone been able to increase the performance with ATI cards?

---

### Post by geneqew on 2010-02-26
same problem here, with HD4670 but with this settings:

compiz on (with effects turned on)
using wine or totem/vlc or any other video playback would slow the system
minimize/maximize of any other window while playing any video is very slow

i tried removing compiz and turned metacity on but it has the same results..

btw current vcard driver is ubuntu's ati driver

---

