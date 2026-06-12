---
title: "GNOME crashing when opening dashboard"
date: 2013-02-24
forum: Desktop Environments
---

### Post by Odzinic on 2013-02-24
Hello,

I recently did a apt-get update and applied about 300mb of updates without really looking them over. After rebooting I started experiencing crashes with GNOME whenever I tried to open the dashboard.

I have tried reinstalling gnome, trying to restart gnome and re-configuring gnome to no avail. Every single time I try to open dashboard it simply crashes.

I am using GNOME 3.6, on Ubuntu 12.10 and have an AMD Radeon 6520G video card. I have been using GNOME for months now without an issue.

Does anyone know of a potential fix for this?

---

### Post by unheeding on 2013-02-26
Do you have Unity installed?  If so, test it out.


Another way to test would be to run glxgears and see if you see the spinning gears (you may have to 'sudo apt-get install mesa-utils') - if it returns an error you may have a problem with your graphics drivers.  Usually GNOME will just refuse to start in 3d mode without working drivers though, so I'm not sure.

---

