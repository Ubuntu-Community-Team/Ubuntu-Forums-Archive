---
title: "philips webcam problems"
date: 2009-02-04
forum: General Help
---

### Post by relaxedcrazyman on 2009-02-04
hello, i have read some other posts, and tried a couple of things, but nothing seems to work. FYI i am super noobie, simple instructions please.

i have my philips webcam plugged in, the light is on, but nothing recognizes it. i tried ekiga, vlc and easycam2. they all say that they are not detecting the webcam. HELP!!!

Thanks!

---

### Post by relaxedcrazyman on 2009-02-06
anyone?

---

### Post by arvevans on 2009-02-06
setpwc

qc-usb-source

qc-usb-utils

qc-usb-modules

[http://www.crazysquirrel.com/computing/debian/webcam.jspx]("http://www.crazysquirrel.com/computing/debian/webcam.jspx")

---

### Post by relaxedcrazyman on 2009-02-06
> **arvevans said:**
> setpwc

qc-usb-source

qc-usb-utils

qc-usb-modules

[http://www.crazysquirrel.com/computing/debian/webcam.jspx]("http://www.crazysquirrel.com/computing/debian/webcam.jspx")


i tried to follow the instructions, but i dont really understand how i do what i need to do. i am so confused.

---

### Post by arvevans on 2009-02-06
It is confusing.  Even the experts have trouble with Phillips Web Cams.  The real problem appears to be that Phillips has not released information on how their camera chip works.  Apparently only Microsoft developers have been able to obtain that information.

The Linux developers then refer to a "qc-usb-modules" which apparently would be the kernel module for interfacing Phillips Web Cams if the information for writing that module were available.  Problem is that the needed info is not available, and thus the "qc-usb-modules" appears to have not yet been written.

However, all is not lost.  If you go to the Synaptic Package Manager and install "qc-usb-utils", that apparently contains a work-around interface module which should talk to your Phillips Web Cam.  You may also need to install "setpwc" if you need to make any setting changes in how your camera operates.

You can also go the the Web and use Google to search for "Phillips Web Cam Linux" and you will find a lot of possibly helpful information.  

I have 2 Phillips Web Cams which are supposedly alike.  Both work with Microsoft-XP, but only one of them has ever worked with Linux, even though both are supposed to be identical.

Hope this helps.

---

### Post by relaxedcrazyman on 2009-02-07
i tried the qc-usb utils, no dice. someone somewhere else suggested, pwc-10.0.12-rc1, i guess it is a driver for the cams, i followed the instructions to the letter, but still not working. it does however work when i am on vista. 

any other ideas?


thanks

---

