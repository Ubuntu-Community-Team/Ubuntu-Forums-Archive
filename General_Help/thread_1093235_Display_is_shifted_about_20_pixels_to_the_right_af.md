---
title: "Display is shifted about 20 pixels to the right after nvidia driver 180.29 install"
date: 2009-03-11
forum: General Help
---

### Post by Shmalignant on 2009-03-11
What the problem is:
With normal or extra visual effects enabled, upon login, the monitor display is shifted about 20 pixels to the right.

When this started:
The problem began when I upgraded from 177.xx to 180.29

What fixes it:
The problem is corrected when I change the screen resolution in nvidia settings (as root) and apply the changes. The fix is only palliative as when I log out the screen shifts back to 20 pixels off center to the right. The GDM login screen is normal.

My computer:
HP Pavilion dv6000
Ubuntu 8.10
Nvidia GeForce Go 7400

---

### Post by fooman on 2009-03-11
check the settings on the monitor itself...i have seen similar instances where the entire display is offset some to the right and pressing the "auto" setting on the *monitor *snaps it right back into place.

---

### Post by Shmalignant on 2009-03-11
> **fooman said:**
> check the settings on the monitor itself...i have seen similar instances where the entire display is offset some to the right and pressing the "auto" setting on the *monitor *snaps it right back into place.

Unfortunately this a notebook and there are no hard settings to manipulate.

---

### Post by fooman on 2009-03-11
are you making the changes to nvidia-settings as root?

in order to make the change "stick"...you need root privileges.

try this in a terminal:

```
gksudo nvidia-settings 
```

make the change,  log out and back in again....see if that works.

---

### Post by Shmalignant on 2009-03-11
> **fooman said:**
> are you making the changes to nvidia-settings as root?

in order to make the change "stick"...you need root privileges.

try this in a terminal:

```
gksudo nvidia-settings 
```

make the change,  log out and back in again....see if that works.

Yes, I have made the changes as root to no avail. :(

---

### Post by fooman on 2009-03-11
after making the resolution change, click on "save to x-configuration file", then "save" in the next box.

see if that works.

sorry if you have already done so....thats all i can think of.

---

### Post by unutbu on 2009-03-11
Shmalignant, please post your /etc/X11/xorg.conf

---

### Post by bubwitmaingay on 2009-03-11
I uninstall the nvidia driver because it also caused an ugly display. When I started using my monitor without the driver, it looks cool and fine but when I used the driver it looks ugly (as in it looks like a Microsoft safemode environment). Then I can't increase the resolution after using the driver while without it I have the best resolution I could get from the settings.

I think you can live without the driver and the 3d effects for your monitor will be boring in the long run. Take that driver off.

Hope that enlightens. 8)

---

### Post by Shmalignant on 2009-03-11
The problem was with the driver.  I updated to the [180.37]("http://www.nvnews.net/vbulletin/showthread.php?p=1951107") pre-release and the problem is solved.  Thank you all for your input!

...Now where's that darn "[solved]" tab????

---

