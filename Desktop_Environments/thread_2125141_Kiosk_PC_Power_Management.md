---
title: "Kiosk PC Power Management"
date: 2013-03-13
forum: Desktop Environments
---

### Post by Axor1 on 2013-03-13
Hello,

I want to configure a kiosk pc with opera in kiosk mode.

so I installed Ubuntu 10.12 minimal with

sudo apt-get install xserver-xorg-core xinit
sudo apt-get install rungetty

tty1.conf: exec /sbin/rungetty –autologin username tty1
.bash_profile: startx
.xinitrc: exec opera --k


everything work well, after booting opera appears in kiosk mode

the problem is, that I found no way to set power management options like power off the monitor or hibernate



Thank you for your help!

---

### Post by Axor1 on 2013-03-13
One more information:
i tried xscreensaver, black screen work after 1 minute but all DPMS function do not work

---

