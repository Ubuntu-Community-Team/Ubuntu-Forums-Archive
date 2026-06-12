---
title: "Dell Inspiron 1420 (japanese)"
date: 2007-06-30
forum: Dell  Ubuntu Support
---

### Post by vladuz976 on 2007-06-30
Hi,
I wanted to buy an Inspiron 1420 from the dell.com/open site with ubuntu preinstalled, but I am in Japan for 3  months and they are not willing to ship abroad for some reason, but I really need this notebook for work right now. I went ahead and customized the Inspiron 1420 on the japanese site to about the same specs, but not everything was available as on the US site.

I was just wondering if Dell uses any restricted drivers to make all the hardware work, that are not available otherwise. Can someone look at my specs and tell me if any there are any known incompatibilities?
My specs are as below:

Intel Core 2 Duo T7100 2MB L2 1.80GHz 800MHz
Japanese keyboard
2GB(1GBx2)DDR2-SDRAM
Intel GMA X3100 chipset
80GB SATA HDD (5400RPM)
90W AC Adapter
DVD+/-RW Drive
14.1 inch TFT True Life WXGA 1440x900 pixel
Dell Wireless 355 Bluetooth
Core 2 Duo PRO/Wireless 3945ABG 802.11a/b/g

also here is a picture of the specs as Dell emailed them to me:
[http://www.vladuz976.com/files/pic1.png](http://www.vladuz976.com/files/pic1.png)

---

### Post by neptho on 2007-06-30
You may have a few problems with the video only working at 1024x768 until you install the 915resolution package, but the 3945 wireless is natively supported, just install the restricted-modules.

2GB RAM and 80GB HD?  Owch.  I suppose OpenOffice will load fairly fast.  :)

---

### Post by fjgaude on 2007-07-01
The 1420 sure looks good to me, and the colors, wow!

The release I read said the 1420 wasn't to start shipping until the 15th of July... I wonder if it can be ordered before that?

Good luck in getting this super notebook with the hi-res screen. All should work after you install the 915resolution software: sudo apt-get install 915resolution.

frank

---

### Post by vladuz976 on 2007-07-01
maybe because I ordered it on the japanese Dell website. They may get it a little sooner.

---

