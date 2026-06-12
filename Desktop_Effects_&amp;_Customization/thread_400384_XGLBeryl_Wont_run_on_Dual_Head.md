---
title: "XGL/Beryl Wont run on Dual Head"
date: 2007-04-03
forum: Desktop Effects &amp; Customization
---

### Post by JSpencer87 on 2007-04-03
I am having problems with xgl, I am running a dual head on an ati radeon 9600. I installed Xgl and beryl before configuring the driver for dual head and everything worked great. i was able to use it. When i configured the driver for dual head with "aticonfig --dtop=horizontal --overlay-on=1" after restart when i would try to log on to the XGL session it would give me an error something like

/etc/gdm/presession/default:your session with WTMP and UTMP running : /USR/X11RG/bin/sessreg -a -w /var/log/wtmp -u /var/run/utemp -x etc etc..

Fatal Server Error: No Screens Found
(gnome-session: 5780) GTK-Warning; "Can't Open Display"

Anyone know what i need to do next?

Thnx
Justin

---

### Post by notromda on 2007-04-08
Check this thread.   There is a limitation of what resolution you can handle in 3d mode.
[http://ubuntuforums.org/showpost.php?p=2421572&postcount=8]("http://ubuntuforums.org/showpost.php?p=2421572&postcount=8")

---

