---
title: "Preferences do not include 1280 x 1024 resolution"
date: 2006-12-16
forum: Desktop Environments
---

### Post by Brian L on 2006-12-16
I'm having a slight problem getting a 1280 x 1024 resolution in Ubuntu 6.06 Dapper Drake.

I got to System > Preferences > Resolution and the resolution options only go up to 1024 x 768.  How would I go about fixing this?

---

### Post by melancholeric on 2006-12-16
You'll have to add the option to /etc/X11/xorg.conf . First, back it up. 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

then, edit it. sudo gedit /etc/X11/xorg.conf

Under Section "Screen" SubSection "Display"

You see all these resolutions there. Add "1280x1024". Then, hit ctrl + alt + backspace to restart X.

If it doesn't work restore the backup. 

sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

---

