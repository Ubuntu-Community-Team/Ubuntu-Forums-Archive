---
title: "Lousy resolution with ASUS VH222H"
date: 2015-02-09
forum: Desktop Environments
---

### Post by Roy_Bettle on 2015-02-09
Picked up a pair of these at a liquidation sale.  Resolution is lousy.  I'm using an nVidia GeForce GTX 550 Ti and XFCE and nVidia drivers version 331.113.  The best, stable resolution I've been able to get is 1024x768; higher resolutions cause the desktop environments to bleed into each other and I should be able to get to 1920x1080.  I did some research here before posting and came across this, closed thread:  

[http://ubuntuforums.org/showthread.php?t=1206337](http://ubuntuforums.org/showthread.php?t=1206337)

In the thread, the poster mentioned coming across some xorg.conf tweaks listed in this thread [http://ubuntuforums.org/archive/index.php/t-425527.html](http://ubuntuforums.org/archive/index.php/t-425527.html) which I have subsequently read through as well as a sub thread or two from other forums.

As I was merrily editing xorg.conf, the thought occurred to me that the instructions listed are over 7 years old.  So, I exited without writing the changes and am posting here to make sure that 7 year old fixes won't break my system.  I'm also hoping there's something simpler that I'm over-looking like, for instance, a driver for the LCDs?  The nVidia control panel has them listed as "CRT-0" and "CRT-1"; possibly this is because I'm using DVI to VGA converters at the card as Fry's doesn't have the DVI to HMDI cables I need?

Does anyone have some guidance for me?  I am not the engineer I was 15 years ago so my comfort level is not all that high that I actually know what I'm attempting to do.

Any help would be much appreciated.  Thanks!

---

### Post by gordintoronto on 2015-02-09
It's the converters. The monitors support DVI, so use DVI cables and your problems should disappear. (Nice monitors, BTW; I bought one for a client last year.)

After making the change (with the power off), Nvidia X Server Settings should identify the monitors under "X Server Display Configuration."

You don't need a driver for your monitors, and you should not need to edit xorg.conf.

---

### Post by Roy_Bettle on 2015-02-09
Thank you!  I did find the correct cables on eBay and so I now wait - impatiently - for them to arrive.  =)

---

