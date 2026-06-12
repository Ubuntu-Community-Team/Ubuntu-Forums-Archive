---
title: "how to duplicate Xubuntu-session settings"
date: 2013-06-03
forum: Desktop Environments
---

### Post by planarian on 2013-06-03
The Xubuntu login screen offers a choice between an optimized "Xubuntu session" and a generic "xfce session." I want the option of running a second instance of x11, but using the settings from the Xubuntu session. Unfortunately, after a lot of searching, I still haven't found a way to launch the Xubuntu session using startx (I always get xfce). Second best would be to import those settings into the xfce session but I can't figure out how to do that either. Apparently older versions of Xubuntu used to keep settings in a file usr/share/xubuntu/session.sh, but the most current version (raring), doesn't appear to have it.

---

### Post by Toz on 2013-06-03
Have a read of [this post]("http://ubuntuforums.org/showthread.php?t=2105703&p=12459424&viewfull=1#post12459424") - specifically the section describing the differences between Xubuntu and Xfce.

If you want the option of running two instances of X11 (one for Xubuntu and one for Xfce), execute:
```
gdmflexiserver
```
...from within the first login to create a second X11 instance (first X11 session will exist in virtual console F7, the second in F8). In this second instance, choose the other option. Make sure you use two different fresh accounts so that you can see the differences.

Xfce uses the files and settings in /etc/xdg/xfce to create the default environment, while Xubuntu uses the files and settings in /etc/xdg/xdg-xubuntu (as well as the extras from xubuntu-default-settings if its installed).

---

### Post by planarian on 2013-06-03
Thanks, Toz, I think this brings me a lot closer to my goal. But I actually want to run **two** Xubuntu x11 sessions. Is there a way to do that? Should I simply replace the contents of /etc/xdg/xfce with /etc/xdg/xdg-xubuntu? (I don't need the plain xfce settings)

---

### Post by planarian on 2013-06-03
Actually, nevermind! Executing gdmflexiserver gives me the login screen,  which allows me to choose another Xubuntu session. Fantastic. I  confess, I don't really understand why this works (isn't gdmflexiserver  for Gnome?), but I'll take it!

---

