---
title: "Where to change resolution for Login-Screen?"
date: 2005-05-06
forum: Desktop Environments
---

### Post by Josef on 2005-05-06
I just installed kubuntu and have the problem that all resolutions are set to 1280x1024 and my monitor only supports this with 60Hz.
I can change the resolution for an user using the KDE controlpanel, but where can I change the resolution for the login-screen?

---

### Post by crmanski on 2005-05-06
This link below might help.  Go to the area in the xorg.conf that is mentioned in the HOWTO and remove the resolutions that you do not want the monitor to display.

HOWTO: Screen Resolution in Hoary 5.04
[http://www.ubuntuforums.org/showthread.php?t=21984](http://www.ubuntuforums.org/showthread.php?t=21984)

---

### Post by crazybill on 2005-05-07
Solution: Edit /etc/X11/xorg.conf

**sudo gedit /etc/X11/xorg.conf**

or **sudu vi /etc/X11/xorg.conf**

or use whatever editor you like.

Go to the **Section "Screen"** and then **SubSection "Display"**

```
 SubSection "Display"
                Depth           1
                Modes           "**1024x768**" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
```

Edit/add/delete  the all  wanted/unwanted resolutions here. Then save.

---

### Post by Josef on 2005-05-07
Well, don't seems like the right way to do this, but it's working.
Thank you :)

---

