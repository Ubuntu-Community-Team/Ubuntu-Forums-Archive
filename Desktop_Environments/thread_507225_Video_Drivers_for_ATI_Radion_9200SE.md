---
title: "Video Drivers for ATI Radion 9200SE"
date: 2007-07-22
forum: Desktop Environments
---

### Post by MacDuff on 2007-07-22
I have been fighting with FireFox running extremely slowly with Ubuntu Feisty. The only suggestion that speeded things up was to install VM Ware server and Install Windows XP.  While it works it seems kind of an awkward way to do things and my screen has quite a bad moire effect doing things this way.

One person suggested installing a different video driver.  My card is an ATI Radion 9200SE and I wonder if anyone has tried installing Linux drivers for this card and have you noticed any improvement in display speed and perhaps in screen appearance? 

If you recommend changing the driver, could you advise a simple, complete procedure for doing that as I am a relative noob to Linux and need all the help I can get.

Thanks

---

### Post by overdrank on 2007-07-22
> **MacDuff said:**
> I have been fighting with FireFox running extremely slowly with Ubuntu Feisty. The only suggestion that speeded things up was to install VM Ware server and Install Windows XP.  While it works it seems kind of an awkward way to do things and my screen has quite a bad moire effect doing things this way.

One person suggested installing a different video driver.  My card is an ATI Radion 9200SE and I wonder if anyone has tried installing Linux drivers for this card and have you noticed any improvement in display speed and perhaps in screen appearance? 

If you recommend changing the driver, could you advise a simple, complete procedure for doing that as I am a relative noob to Linux and need all the help I can get.

Thanks

Hi have you enabled the restricted drivers in feisty? If so you may search the forums and find a better options. 
You can try this option also,
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
I know it is a "how to " for beryl but you can use the first part to install the drivers for you graphics card. Good luck! :)

---

### Post by MacDuff on 2007-07-22
Thanks I will have a look at restricted drivers tomorrow.  The moire effect seems to have gone away spontaneously or at least is diminished.  Can't understand why some things seem to sort themselves out given time. 

I will wait to see if anyone has actually changed drivers for this video card and what the effect was before I make any changes that might screw up my system.

---

### Post by overdrank on 2007-07-23
> **MacDuff said:**
> Thanks I will have a look at restricted drivers tomorrow.  The moire effect seems to have gone away spontaneously or at least is diminished.  Can't understand why some things seem to sort themselves out given time. 

I will wait to see if anyone has actually changed drivers for this video card and what the effect was before I make any changes that might screw up my system.

Hi and you are right there is a good chance that when you change anything in your xorg it is possible to crash the xorg so back your xorg and then you can always reconfigure it withthe command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
After you get the blue screen of the xrog failed. Good luck!

---

