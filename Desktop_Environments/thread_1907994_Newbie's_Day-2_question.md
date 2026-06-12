---
title: "Newbie's Day-2 question"
date: 2012-01-12
forum: Desktop Environments
---

### Post by chenxinghao on 2012-01-12
Installed the CCSM application and followed the instructions in Ubuntu Help, trying to down size the icons in the Launcher pad to 32, but the change made no difference - still the same as the default setup.

I installed Ubuntu 11.10 just a day ago and am trying to free up the Launcher space for more applications.

---

### Post by freebird54 on 2012-01-12
I am not an expert on possible problems with this system yet, but the one question does arise.  Are you sure that you are in the 3D mode of Unity? Do other changes you may have made in CCSM make the difference you expect?

Hope it helps :)

---

### Post by grahammechanical on 2012-01-12
The install CD does not include proprietary video drivers. So, when we log in for the very first time we are loading Ubuntu 2D unless the open source drivers that are installed are doing a very good job.

You may need to go to Additional drivers and activate a proprietary driver. There may even be an icon of a video card in the top panel to click.

When the driver is installed and activated try logging out or re-starting and at the log in screen Click the cog or gear icon and you should see both Ubuntu and Ubuntu 2D. click Ubuntu and now see if those changes you made through CCSM work.

Ubuntu (unity 3D) uses Compiz as the compositing or window manager and so Compiz Configuration Settings Manager works in Ubuntu 3D. But Ubuntu 2D uses a window manager called Metacity and so CCSM does not work with it.

Regards.

Regards.

---

### Post by chenxinghao on 2012-01-12
I have not installed anything manually on my own yet.
 
On day-1 right after a fresh install of Ubuntu (burned the CD first and run the installation from it) 11.10, the machine had automatically installed 287 updates without asking me. After that, I went into the Dash home and clicked on "More Apps" -> "Additional Drivers" and it did not detect/install any new drivers.
 
On day-2, I installed and ran CCSM, trying to reduce the Launcher icons' foot prints, apparently without success.
 
I have not manually changed anything other than installed VLC and CCSM.

---

