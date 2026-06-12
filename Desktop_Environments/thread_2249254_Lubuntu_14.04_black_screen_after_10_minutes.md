---
title: "Lubuntu 14.04 black screen after 10 minutes"
date: 2014-10-20
forum: Desktop Environments
---

### Post by orestis-0 on 2014-10-20
Hello, I unchecked every option in the light locker(even deleted it) and power manager for making the screen black. It still continuous to do it even when I watch videos in full screen. From what I searched a lot of people have the same problem but did not find any useful answers. Can you please help me? 
Thank you!

---

### Post by Dennis N on 2014-10-21
The 10 minute time you mention points to DPMS (Display Power Mangement Signaling) as the problem. 

This solution worked for me (from link below) - install xscreensaver and set it to autostart in Lubuntu's startup applications. Also I disabled light locker and set power manager to never put the monitor to sleep.
[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1193716/comments/15](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1193716/comments/15)
It works because Xscreensaver overrides DPMS. From Arch Wiki:
> XScreenSaver manages display energy saving (DPMS) independently of X itself and overrides it. To configure the timings for standby, display poweroff and such, use xscreensaver-demo or edit the configuration file manually, e.g. ~/.xscreensaver
source: [https://wiki.archlinux.org/index.php/XScreenSaver](https://wiki.archlinux.org/index.php/XScreenSaver)
Settings dialog for xscreensaver: **Preferences > Screensaver**
Autostart command for xscreensaver: **xscreensaver -no-splash**

---

### Post by orestis-0 on 2014-10-22
I tried it.... Didn't work...

---

