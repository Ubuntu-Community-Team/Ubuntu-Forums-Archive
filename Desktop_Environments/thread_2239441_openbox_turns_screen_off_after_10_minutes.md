---
title: "openbox turns screen off after 10 minutes"
date: 2014-08-13
forum: Desktop Environments
---

### Post by Frozin1234 on 2014-08-13
Hello,

I am using lubuntu and openbox that has xbmc autostarting. When viewing a show or movie using chrome in full screen the tv screen turns off. I've searched and tried different things to stop this from happening. 

Some of the things i've tried that aren't working are
lightson.sh script 
adding [COLOR=#333333][FONT=sans-serif]xset -dpms s off to the autostart script.

Everything else i've read is mostly to use the above. I have been able to stop the logon screen from coming up after the screen goes black, now I just need it to stop gong black.

Any help would be appreciated.

Thanks.


[/FONT][/COLOR]

---

### Post by Dennis N on 2014-08-13
With the 10 min time you give, sounds like the Display Power Management Signaling (DPMS) at work.

This solution worked for me (from link below) - install xscreensaver and set it to autostart in Lubuntu's startup applications. Also I uninstalled light locker and set power manager to never put the monitor to sleep.

[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1193716/comments/15](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1193716/comments/15)

It works because Xscreensaver overrides DPMS. From Arch Wiki:

> XScreenSaver manages display energy saving (DPMS) independently of X itself and overrides it. To configure the timings for standby, display poweroff and such, use xscreensaver-demo or edit the configuration file manually, e.g. ~/.xscreensaver
source: [https://wiki.archlinux.org/index.php/XScreenSaver](https://wiki.archlinux.org/index.php/XScreenSaver)


---

### Post by Frozin1234 on 2014-08-14
Thanks for the quick response. Ill give it a try and report back tomorrow

---

