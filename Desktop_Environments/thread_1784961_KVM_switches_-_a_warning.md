---
title: "KVM switches - a warning"
date: 2011-06-17
forum: Desktop Environments
---

### Post by mistertransistor on 2011-06-17
For a couple of weeks now I've been fighting to get Ubuntu to use my monitor at a decent refresh rate. I've failed, because my PC has an old Nvidia card, and it seems that Ubuntu simply wont deal with those- the forums are full of people with problems and lots of 'solutions' that don't really work. The proprietary driver just screws everything, and even after manual editing of xorg.conf, it won't behave reasonably.
   However, one thing I've realised - I was using a KVM switch to connect my keyboard/VDU/mouse to multiple systems. This is NOT transparent to Ubuntu, although it *is* to Windows XP. Removing the switch improved my screen resolution in Ubuntu, although it did *not* improve the refresh rate, which is still the real problem. 
   It's very disappointing that moving to Linux is made so hard.

Andrew

---

### Post by pricetech on 2011-06-17
I've used KVMs on several occasions and never had an issue.  One's mileage may vary, as they say.

You don't mention what type KVM you have.  Some of the mechanical ones don't properly "load" the computer when switched away from it.  That may be part of the problem.

You might also try making sure the KVM is addressing the Linux box when you boot it.

---

### Post by tgalati4 on 2011-06-17
Did you add the appropriate modeline to your xorg.conf?  If you want to run 1600x1200 @ 85 Hz then:

gtf 1600 1200 85


tgalati4@tpad-Gloria7 ~ $ gtf 1600 1200 85

  # 1600x1200 @ 85.00 Hz (GTF) hsync: 107.10 kHz; pclk: 234.76 MHz
  Modeline "1600x1200_85.00"  234.76  1600 1720 1896 2192  1200 1201 1204 1260  -HSync +Vsync

---

### Post by bboggess on 2011-06-18
I have been running a Belkin 4 port KVM switch for over 5 years now.  Currently I have 4 boxes running off the switch to an older style CRT monitor.  This multi-sync monitor is capable of 1600 x 1200 @ 75 hertz.  I have 2 Ubuntu boxes that have video cards capable of this display rate, 1 SuSe box and 1 Windows Box running different display rates. The Windows box is running 1280 x 1024 and the SuSe box is only capable of 1024 x 768 @ 60 hertz.  

I have NO problems switching back and forth between boxes.  The keyboard, mouse, and monitor all respond properly.

Your mileage may vary...

Bill

---

### Post by tgalati4 on 2011-06-18
Understand that a VGA KVM will normally have a 1600 x 1200 @ 85 Hz limitation.  Trying to run your high definition wide screen (1920 x 1080 at 60 Hz) will cause problems.

---

### Post by coffeecat on 2011-06-19
As the OP has not logged in again since posting, they may or may not ever read the replies, but I'll add one other point. My Aten CS1782 KVM works just fine with Windows, Linux and MacOS. Perhaps that's because the User Manual states:

> Multiplatform support - Windows 2000/XP/Vista, Linux, Mac and SunAnd as a footnote clarifies that the Linux support is for kernel 2.6 and higher.

As always, research any hardware you buy for Linux compatibility and don't be surprised if you need to do some work if the manufacturer of the hardware can't be bothered to ensure that their hardware is Linux-compatible. Most KVM switches are not just simple mechanical switches. They have firmware that must communicate with the host machine OS. I don't know what Linux kernel modules are involved, but this is clearly a complex issue.

---

