---
title: "no desktop"
date: 2007-09-18
forum: Desktop Effects &amp; Customization
---

### Post by mpcrsc562 on 2007-09-18
i installed ubuntu last night. i was trying to enable desktop effects, but kept getting an error message (can't remember for sure, but it was about composite something or another). so, i added glDesktop by way of synaptics. all was cool. by the way, i am using an acer aspire 5100 with ati radeon xpress 1100 graphics. i had the restricted drivers enabled, but could not do a thing as far as desktop effects. i ran the glDesktop and still could not get desktop effects. i went back to the restricted drivers and disabled the ati driver and rebooted (glDesktop was still running). when my computer rebooted, the login and password screens were fine. the box that displays nautilus showed for a few seconds then the screen went black for a few seconds then totally white. i have no desktop and do not know how to reset my display settings by way of safe mode. any help?

---

### Post by AndrewGene on 2007-09-18
press ctrl+alt+backspace, this will take you to the login screen.  Then go to actions and log on without running start up scripts.

---

### Post by mpcrsc562 on 2007-09-18
i had read another post earlier and tried:
     sudo dpkg-reconfigure xserver-xorg
now i have no gui logon. what do i do to not have to reinstall ubuntu? or is that the best course of action?

i retried sudo dpkg-reconfigure xserver-xorg. i paid close attention to what i was doing and went thru the whole process. i was able to get the gui logon screen again. i tried to logon normally but got the black then white screen. i went to options>session>gnome failsafe but got the same thing as a normal logon. i went back to the logon screen and logged on by way of terminal failsafe. i opened /etc/x11/xorg.conf, but do not know what, if anything, i am supposed to look for or change. where do i go from here?

---

### Post by mpcrsc562 on 2007-09-18
i reinstalled ubuntu. all is ok. thanks for your help.

---

