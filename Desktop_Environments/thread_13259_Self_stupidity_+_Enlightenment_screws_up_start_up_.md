---
title: "Self stupidity + Enlightenment screws up start up script."
date: 2005-01-30
forum: Desktop Environments
---

### Post by Lachlan on 2005-01-30
After installing Enlightenment,rebooted,looked in session menu,no Enlightenment.Fired up Enlightenment from Nautilus and a box appeared and gave me a choice of setting up Enlightment in the start up script (or something similar),pressed yes (in hindsight a big mistake) .Logged out and found that Enlightenment had taken over the session menu apart from Failsafe Gnome.Removed Enlightenment,rebooted and tried to run Gnome: error.      This session only lasted less than 10 seconds.If you have not logged out yourself,this could mean that there is some installation problem or that you may be out of diskspace.
Try logging in with one of the failsafe sessions to see if you can fix this problem.
	View details (~/.xsessions-error file)

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "lachlan"
/etc/gdm/Xsession: Beginning session setup...
/home/lachlan/.xsession: line 2: /usr/bin/enlightenment: No such file or directory
/home/lachlan/.xsession: line 2: exec: /usr/bin/enlightenment: cannot execute: No such file or directory

Log in with failsafe Gnome:    This is the failsafe Gnome sessions.You will be logged into the Default session Gnome with no start up scripts run.This is only to to fix the problem in your installation.
	I have no idea what file to alter,and how to alter it to get me back to a working session menu.

Lachlan. :oops:

---

### Post by llamakc on 2005-01-30
In the error it gave you it mentioned a file called /home/lachlan/.xsession and line number 2. Open that file up in your editor of choice and see if tinkering there can help. FWIW, you can add your own custom xsessions also in /usr/share/xsessions/. I usually tweak one of those to point to a customized startup script...

But for now, look at ~/.xsession and line #2. Looks like that is where the change was made.

---

### Post by Lachlan on 2005-01-31
Thanks for the push in the right direction.

---

