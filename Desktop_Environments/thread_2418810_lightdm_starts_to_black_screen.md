---
title: "lightdm starts to black screen"
date: 2019-05-11
forum: Desktop Environments
---

### Post by baudio on 2019-05-11
I have XUbuntu 19.04 installed as a VirtualBox VM. Things were working fine, until a reboot, and now lightdm doesn't start properly. The machine boots directly to a blank/black screen, which I believe is X11/Xorg on VT7. I can get to the console with HOST+F1. When I log in on the console, it shows lightdm is running. If I type "sudo service lightdm restart", then lightdm comes up as expected.

I tried reinstalling the virtualbox guest utilities, re-adding lightdm to the default runlevel, running "dpkg-reconfigure lightdm" (which appears to do nothing), removing the pid file in /var/run/lightdm.pid. But none of that worked. I'm about out of ideas. Does anybody know what else might be causing this to not start up correctly on boot?

Thanks!

---

