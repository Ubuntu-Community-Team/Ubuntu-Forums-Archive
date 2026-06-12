---
title: "Compiz not working"
date: 2010-07-13
forum: Desktop Environments
---

### Post by blueysak on 2010-07-13
I just installed ubuntu and I installed compiz but nothing is working. Do I have to install my graphics card? If so how do i? When I go to hardware drivers it says "No proprietary drivers are in use on this system." The internet is working, I am posting this from ubuntu.

---

### Post by krishnandu.sarkar on 2010-07-13
Hmm...You need to install your Graphics Card driver.

---

### Post by blueysak on 2010-07-13
> **krishnandu.sarkar said:**
> Hmm...You need to install your Graphics Card driver.

how?

---

### Post by mildlyAmused on 2010-07-13
Ati's driver for older/ pre DX10 video cards isn't supported by newer versions of Ubuntu. If you were using Ubuntu 8.0.4  this would be a non-issue.

---

### Post by bigsmitty64 on 2010-07-13
Maybe start by typing this in terminal:

```
lspci | grep -i vga
```
It will tell you what graphics you have. Post the output here.

Then we (someone) can better help you.

---

### Post by blueysak on 2010-07-13
> **bigsmitty64 said:**
> Maybe start by typing this in terminal:

```
lspci | grep -i vga
```
It will tell you what graphics you have. Post the output here.

Then we (someone) can better help you.

I did lspci and i got

```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:05.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:05.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:06.0 FireWire (IEEE 1394): Texas Instruments TSB12LV23 IEEE-1394 Controller
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
```

I didnt do the others (this code I already had)

---

### Post by Pogeymanz on 2010-07-13
What do you mean by "nothing is working?" Do you still boot into a graphical desktop but there are no special effects? Are there still window decorations on the windows (the titlebar, close button, etc)?

Try, from a terminal, running: 
```

compiz --replace

```

And telling us the output.

You probably don't need to reinstall the graphics driver since Intel's graphics play nice in Linux.

---

### Post by blueysak on 2010-07-13
> **Pogeymanz said:**
> What do you mean by "nothing is working?" Do you still boot into a graphical desktop but there are no special effects? Are there still window decorations on the windows (the titlebar, close button, etc)?

Try, from a terminal, running: 
```

compiz --replace

```

And telling us the output.

You probably don't need to reinstall the graphics driver since Intel's graphics play nice in Linux.


I got this
```
Blacklisted PCI ID 8086:2562 detected

Launching fallback window manager

```

---

### Post by Pogeymanz on 2010-07-14
Apparently that particular card has some issues with the current version of Compiz I guess.

Check this out to try it anyway:
[http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

Otherwise, maybe try an older intel driver, or the super-new version of Compiz.

---

### Post by blueysak on 2010-07-14
> **Pogeymanz said:**
> Apparently that particular card has some issues with the current version of Compiz I guess.

Check this out to try it anyway:
[http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

Otherwise, maybe try an older intel driver, or the super-new version of Compiz.
How would i get the newest version and does it work with my driver?

---

### Post by andrea000 on 2010-07-15
if your looking to unblacklist the card you could also install ghex or any hex editor and look for the card near the bottom on the right side it should be there change one of the numbers and your done.

---

### Post by blueysak on 2010-07-15
> **andrea000 said:**
> if your looking to unblacklist the card you could also install ghex or any hex editor and look for the card near the bottom on the right side it should be there change one of the numbers and your done.
Is hex in the ubuntu software store or where? And are there any certain steps I need to follow or is it just downloading and installing?

---

