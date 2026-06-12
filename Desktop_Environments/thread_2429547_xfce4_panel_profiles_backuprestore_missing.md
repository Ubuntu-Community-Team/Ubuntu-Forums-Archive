---
title: "xfce4 panel profiles backup/restore missing"
date: 2019-10-19
forum: Desktop Environments
---

### Post by rattskjelke on 2019-10-19
I installed Xubuntu 19.10 the other day and must have done something to break the xfce4-panel settings.
When I go to Panel Preferences the Profiles: *Backup and restore* button is gone.
Can anybody tell me how to fix this or what program provides the button?

---

### Post by Holger_Gehrke on 2019-10-19
I don't know what happened to the button in 19.10, but the program for saving and restoring panel settings called by the button on 18.04 is /usr/bin/xfpanel-switch, a shell script calling a python script ('/usr/share/xfpanel-switch/xfpanel-switch/xfpanel-switch.py'), from the package xfpanel-switch which is available in the standard repos for 18.04. A bit of searching leads me to believe this has been replaced in 19.04 with a package named xfce4-panel-profiles containing a program of the same name. You could check whether that is installed and calling it directly if it is.

Holger

---

### Post by rattskjelke on 2019-10-19
> **Holger_Gehrke said:**
>  A bit of searching leads me to believe this has been replaced in 19.04 with a package named xfce4-panel-profiles containing a program of the same name. You could check whether that is installed and calling it directly if it is.
That is correct. 19.10 is the same.

I broke something that removed the *Profiles: Backup and Restore* button. I reinstalled Xubuntu 19.10 today and it is back to normal.

---

