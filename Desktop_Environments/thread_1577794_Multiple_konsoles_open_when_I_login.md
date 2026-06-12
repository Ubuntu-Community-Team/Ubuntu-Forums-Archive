---
title: "Multiple konsoles open when I login"
date: 2010-09-19
forum: Desktop Environments
---

### Post by bnistor on 2010-09-19
For a while now, every time that I log back into my desktop from hard start or from restarting the X server, I get these 3 terminal konsole windows that are open on my first desktop environment. It's seems as though whatever work I was doing when I had those 3 konsole windows open got saved somewhere and is reopening them every time I get back onto the desktop. I've tried to locate the problem by looking in .bash_profile and .bashrc but to no avail. If anyone has a solution to this, that would be awesome. Thank you in advance.

---

### Post by Zorael on 2010-09-19
You probably have your environment set up to restore a **session** that has three Konsoles running. Is this in KDE? Your thread tag says **[COLOR="Orange"][ubuntu][/COLOR]**, but Konsole is a KDE program. Nevertheless, nothing's stopping anyone from running Konsole in GNOME.

In KDE, just enter 'session' in a run box (Alt+F2) and pick Session Management (or find it in System Settings). In there, check Start with an empty session.

I imagine there's a similar Sessions section to GNOME's Preferences or Advanced menu lists.

---

