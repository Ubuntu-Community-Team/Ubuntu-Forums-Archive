---
title: "GNOME hangs during booting (again)"
date: 2005-04-28
forum: Desktop Environments
---

### Post by davegahan on 2005-04-28
I have after a fresh install of Ubuntu Hoary the following problem: after installing some applications, updating multimedia codecs and updating the looks of GNOME through installing new fonts..... I log out of GNOME, restart and.... GNOME  hangs during the loading of "metacity window manager". This is the second time this happens.

I can get into GNOME with failsafe session, one that disables startup scripts. How do I find out where the culprit is that makes GNOME hang ? Or, how can I go back to the fresh install I had before ?

++ [COLOR=Red]What I did I went to my home folder and switched to view all hidden files. Went to my gnome session files in .gnome2.0. I renamed the session file to "dummy" and the problem went away. I'll send however a copy of it to the developers through bugzilla[/COLOR]

---

### Post by nad on 2005-04-28
Read your log files /var/log/gdm/:0.log and ~/.xsession-errors .

---

