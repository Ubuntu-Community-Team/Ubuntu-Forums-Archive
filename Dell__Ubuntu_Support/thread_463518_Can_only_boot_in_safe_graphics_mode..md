---
title: "Can only boot in safe graphics mode."
date: 2007-06-03
forum: Dell  Ubuntu Support
---

### Post by Aviator_14 on 2007-06-03
Hello. I am new to linux and ubuntu I downloaded the ubuntu desktop 7.04 iso cd image from the ubuntu website and burned it to a cd but when i boot from the cd and click start or install ubuntu it loads and shows a whole bunch of green vertical lines on the screen and thats it I can't see anything else no desktop or anything. But when I go to safe graphics mode it works just fine. The graphics are also fine in Windows XP so I know its not my video card or monitor. So why can I only boot in safe graphics mode. 
P.S. when I boot in safe graphics mode it says something about a restricted driver not compatible or something so could that be the problem that the video card driver isn't compatible with linux? I hit enable driver and it downloaded it  but I still had the same problem trying to boot in normal mode.
Here is a screenshot of what the notice says.

---

### Post by Paul S on 2007-06-04
Looks like you have an nvidia card.  Yes, the proprietary nvidia driver is not supported on the live cd.  But, it still should boot up using either the free nv driver or the free vesa driver.  I do not have experience with the nvidia card on feisty, as mine is ATI, which also is not supported.

You can search this forum or check the wiki to find howto's for installing nvidia drivers and configuring xorg.conf.  I do not know if this will work while you are using the live cd or not.  But, after you do an installation, you can install the proper driver and it will work.

HTH

---

### Post by stchman on 2007-06-04
> **Aviator_14 said:**
> Hello. I am new to linux and ubuntu I downloaded the ubuntu desktop 7.04 iso cd image from the ubuntu website and burned it to a cd but when i boot from the cd and click start or install ubuntu it loads and shows a whole bunch of green vertical lines on the screen and thats it I can't see anything else no desktop or anything. But when I go to safe graphics mode it works just fine. The graphics are also fine in Windows XP so I know its not my video card or monitor. So why can I only boot in safe graphics mode. 
P.S. when I boot in safe graphics mode it says something about a restricted driver not compatible or something so could that be the problem that the video card driver isn't compatible with linux? I hit enable driver and it downloaded it  but I still had the same problem trying to boot in normal mode.
Here is a screenshot of what the notice says.

Check that box next to the nvidia driver and your card will then work properly.

Also this is the Dell section, you should put a thread like this in the General Help section.

---

