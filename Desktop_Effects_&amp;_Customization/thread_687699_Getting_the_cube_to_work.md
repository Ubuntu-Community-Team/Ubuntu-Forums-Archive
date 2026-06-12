---
title: "Getting the cube to work"
date: 2008-02-04
forum: Desktop Effects &amp; Customization
---

### Post by drdmac1 on 2008-02-04
Very new. Can't get the cube to work. Video card Nvidia Geforce 7950GT. The windows wobble when I pull them round and I have 4 workspaces selected. Somewhere else I read that I had to enable "glx". I ran the command as follows 

david@david-desktop:~$ sudo nvidia-glx-config enable

and got this response

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

Is anybody able to comment please?:confused:

---

### Post by FuturePilot on 2008-02-04
If Compiz is running, then everything is working fine. You don't need to modify your xorg.conf. You need to install Compizconfig
```
sudo apt-get install compizconfig-settings-manager
```
Then go System&#8594;Preferences&#8594;Advanced Desktop Effects Settings. There you can enable the cube and many other plugins :)

---

### Post by drdmac1 on 2008-02-04
Thank you. The CompizConfig Settings Manager is already available. "Desktop Cube" and "Rotate Cube" are selected but still no cube on the descktop.

---

### Post by ed-koala on 2008-02-04
Try this link, nice tutorial for getting things working in Compiz:
[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty")

---

### Post by FuturePilot on 2008-02-04
You might have to configure some of the options. Just click on the plugin to configure it.

---

