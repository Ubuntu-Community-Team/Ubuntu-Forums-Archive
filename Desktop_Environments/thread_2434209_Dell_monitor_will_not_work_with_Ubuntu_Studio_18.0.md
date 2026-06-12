---
title: "Dell monitor will not work with Ubuntu Studio 18.04"
date: 2020-01-01
forum: Desktop Environments
---

### Post by Music_Guy on 2020-01-01
I have a Dell U2717D monitor.  I hooked it up to both a 2011 iMac and a Dell Latitude E6440 laptop running Ubuntu Studio.  I connected the iMac to the monitor with a Dell miniport-to-HDMI cable, and the laptop with an HDMI-to-HDMI cable.  In both instances, I could see the Ubuntu Studio login screen.  However, when I logged in, all that I see is the Ubuntu Studio 18.04 logo.  There is no dock, no icons, nothing.  I also could not see any open apps.  Changing the resolution on the computers did not help.  There were no settings on the monitor (except screen ratios, 16:9, 5:4, and 4:5) available.  These did not help either.  I tested both with Ubuntu Studio 19.10 (I think) and both worked.  What can I do to actually see items on the monitor.

---

### Post by Autodave on 2020-01-01
I am a little confused here: are you saying that everything works OK when you boot to 19.10?  If so, you may need to use 19.10 because it has newer drivers in it.

---

### Post by Music_Guy on 2020-01-02
I found out the reason that the monitor did not seem to work with Ubuntu Studio 18.04.  I had the "primary display" box checked.  When I unchecked this box, the monitor sprang to life and is working perfectly now.

---

