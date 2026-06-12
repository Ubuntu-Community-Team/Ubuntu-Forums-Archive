---
title: "[SOLVED] video card problems"
date: 2007-09-08
forum: Desktop Environments
---

### Post by offroad64 on 2007-09-08
I upgraded my video card from an ATI All in wonder 2006 series to a GeForce 8400 series.
I wanted to be able to run a 3d desktop. I used "Envy" to remove the old ATI drivers and to install the new Nvidia drivers. I use the Nvidia X Server Settings to set the resolution @ 1280x1024
for a 19" Sceptre monitor. When I save I get a message "Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.
When I shut down and restart the monitor defaults to 1024x768
Does anybody know how I can remove the old backup file so I can replace it with the new settings?

Thanks
Offroad64

---

### Post by IanW on 2007-09-09
sudo rm /etc/X11/xorg.conf.backup

or just in case of error, rename it with

sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf.backup-1

---

### Post by offroad64 on 2007-09-09
I tried and this is what I got. I renamed the file to "xorg.conf.backup-1" and using the files browser I can see it worked. This is the message I get now "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

---

### Post by offroad64 on 2007-09-09
I got it to work
I had to reconfigure xserver from recovery mode.
All is good now
Thank you

---

### Post by Evanlec on 2007-09-09
any simpler way to save the configuration from the nvidia-settings panel?
heard someone talking about using xhost + and su but when i type su and enter password i get authentication failure (I'm guessing because ubuntu doesnt have a root user?)

*edit* okay figured it out
just did

sudo nvidia-settings

---

