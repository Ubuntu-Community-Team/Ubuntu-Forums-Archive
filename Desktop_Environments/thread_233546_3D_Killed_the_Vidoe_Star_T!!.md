---
title: "3D Killed the Vidoe Star T!!"
date: 2006-08-10
forum: Desktop Environments
---

### Post by galego on 2006-08-10
I enabled my 3D accel. last night and....well is did not accel. it kept my x console from opening. tried to reconfigure xorg, and I killed it! --- got frustrated so i just re-installed ubuntu :sad: !

I followed this:
[https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)

and got this:
 "X console could not start; reconfigure your xorg file"

actualy this was the same message I got when i was first trying the Live cd, and now i understand it was the 3d driver not the video card (ATi Radeon X700Pro PCie); as it was enabled in MEPIS. 

so my question is, what precautionary steps should i have taken to make the 3D eccel. happen? I followed the steps and when going through the options of xserver-xorg it auto detected all of my video settings; not sure what to do. 

Thanks for any help you can provide!

---

### Post by maniacmusician on 2006-08-10
well ATI cards are always a pain to set up correctly; i have one too. I would recommend at first trying automated scripts like EasyUbuntu (I don't think Automatix has ATI...only Nvidia) to install the driver. [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

and if that doesn't work, try some of the guides and howtos that are scattered about

---

### Post by galego on 2006-08-10
> **maniacmusician said:**
> well ATI cards are always a pain to set up correctly; i have one too. I would recommend at first trying automated scripts like EasyUbuntu (I don't think Automatix has ATI...only Nvidia) to install the driver. [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

and if that doesn't work, try some of the guides and howtos that are scattered about

have you used easy ubuntu for video driver install?

and why oh, why did i not know about easy ubuntu before, if it does what it says it sure would be easier than going all over the wiki to get multimedia support!!

---

### Post by maniacmusician on 2006-08-10
yes i have tried it and it worked well for me. i did not attempt 3D hardware acceleration though, i was just looking to fix some resolution problems. but those did get solved

---

