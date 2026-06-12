---
title: "Gnome reports wrong screen refresh rate"
date: 2007-01-06
forum: Desktop Environments
---

### Post by Lemmus on 2007-01-06
Gnome reports wrong screen refresh rates on my nvidia 7900glx.
I cannot find any system in what it reports. 1920x1440@85 is reported as 57 Hz whereas 1600x1200@85 Hz is reported as 51 Hz.
I am using nvidia's driver but on their forum they say that the bug is in gnome.
(nvidiasettings report correct refresh-rate)

---

### Post by Domie on 2007-01-17
Good question...

---

### Post by floke on 2007-01-17
I've had this problem several times on various machines.
You could try eithe (from terminal)

sudo nano /etc/X11/xorg.conf (will enable you to edit the xorg.conf file where the settings are kept), or

sudo dpkg-reconfigure -phigh xserver-xorg (will allow you to reset the file and enter new settings - be sure to use the space bar to select the highest resolution you can have).

Also - be sure to make a backup of the xorg.conf file before editing it in case anything goes wrong. There's a good and fast way of doing this via the terminal but I don;t know it. My much slower method is to use 'gksudo nautilus' (run nautilus in root mode), move up to the /etc/X11 directory, and copy the xorg.conf file that way (right click, copy).

One thing you might notice in the xorg.conf file is that it might have selected your monitor as 'generic monitor' - in this case you might have to enter the correct details for it, along with the proper refresh rates. More details on how to do this can be found elsewhere in this form - e.g. search for, say, refresh rates etc.

Hope this helps

---

