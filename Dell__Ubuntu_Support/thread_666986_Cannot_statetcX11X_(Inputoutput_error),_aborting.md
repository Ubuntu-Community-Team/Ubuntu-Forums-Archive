---
title: "Cannot stat/etc/X11/X (Input/output error), aborting"
date: 2008-01-13
forum: Dell  Ubuntu Support
---

### Post by dontke on 2008-01-13
Hey,
I started my DELL C600 laptop, but couldn't go past a screen that said:
[CENTER]Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?[/CENTER]
Then an option of yes and no, when i choose yes:
[CENTER]X: unable to open wrapper config file /etc/X11/Xwrapper.config
X:cannot stat /etc/X11/X (Input/output error), aborting.[/CENTER]
and then an option of ok.
Then another error message after selecting ok:
[CENTER]The X server is now disabled. Restart GDM when it is configured correctly.[/CENTER]
with an ok. After selecting ok a blank screen with a blinking cursor comes up, but I cant type any commands here.
I restart and use the recovery mode when on the command line, I try to ```
sudo dpkg-reconfigure xserver-xorg
``` but I get another error message> /var/lib/dpkg/info/xserver-org.prerm: 160: awk: Input/output error
/var/lib/dpkg/info/xserver-org.config: 156: awk: Input/output error
/var/lib/dpkg/info/xserver-org.config: 1326: awk: Input/output error
/var/lib/dpkg/info/xserver-org.config: 1395: awk: Input/output error Please help, Im not that good in linux so please use "lame mans language"

---

### Post by m94mni on 2008-01-14
I/O error sounds like a hard drive failing.

Back up all your important data immediately, and then boot from a LiveCD and run a disk check.You might need to replace your HDD.

---

