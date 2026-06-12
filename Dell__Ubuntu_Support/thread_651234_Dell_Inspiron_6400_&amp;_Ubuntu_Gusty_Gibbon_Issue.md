---
title: "Dell Inspiron 6400 &amp; Ubuntu Gusty Gibbon Issues"
date: 2007-12-27
forum: Dell  Ubuntu Support
---

### Post by deepank on 2007-12-27
Hi,

Although many things worked out of the box with some sort of graphics also detected. Some issues that are there with my newly installed Gusty Gibbon on my Dell Inspiron 6400 laptop are :

1. No splash screen is shown while booting up and my screen goes black for about 30 seconds and then my login screen comes up.

2. I cannot hibernate the laptop. Whenever I click on hibernate screen goes blank and remains as it is till I manually power down the laptop.

I have a ATI Radeon Mobility X1400 Graphics Card. Also the sound quality is not as good as it should have been. Should I install some other sound drivers too?

---

### Post by Paul S on 2007-12-28
> **deepank said:**
> Dell Inspiron 6400 laptop are :

1. No splash screen is shown while booting up and my screen goes black for about 30 seconds and then my login screen comes up.

2. I cannot hibernate the laptop. Whenever I click on hibernate screen goes blank and remains as it is till I manually power down the laptop.

I have a ATI Radeon Mobility X1400 Graphics Card. Also the sound quality is not as good as it should have been. Should I install some other sound drivers too?

1. The ATI X1400 is a problem because the only open source driver is "vesa".  Vesa doesn't do much but get you a screen image.  After you install and reboot, you can activate the "restricted driver" fglrx, which provides 3D support.  Unfortunately, the boot splash screen size was probably set up during the time the "vesa" driver was in use.  So you need to edit /etc/usplash.conf and change  the x and y to something closer to your actual screen size, then run "sudo dpkg-reconfigure usplash" and reboot.

2. Unfortunately, the fglrx driver in gutsy does not support suspend / resume.  So, your best bet is to upgrade to the latest from ATI.  Check out this link for howto:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

It fails to meantion that you have to edit /etc/default/acpi-support to change POST_VIDEO=false (in place of true).

I didn't have any problem with sound, so don't have an answer to that.

HTH

---

### Post by deepank on 2007-12-29
Thanks a lot ... 
Its not that there is a problem with sound but the quality of sound is somewhat less than that of Windows XP. But I think I can live with it and its not much noticeable.

---

