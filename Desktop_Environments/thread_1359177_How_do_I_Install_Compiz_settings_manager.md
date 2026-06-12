---
title: "How do I Install Compiz settings manager?"
date: 2009-12-19
forum: Desktop Environments
---

### Post by LinuxBob on 2009-12-19
I just re-installed 9.04 and plan to now upgrade it to 9.10.  I used Synaptic search on Compiz and all the results were green boxed (already installed).  But I don;t see Compiz settings manager under System>Preferences or Administration.

When I search synaptics for ccsm or simple-ccsm or emerald nothing returns.  

I ran this and got these results in terminal:

administrator@dell-desktop:~$ sudo apt-get install ccsm
[sudo] password for administrator: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
administrator@dell-desktop:~$ 

nVidia proprietary driers are installed and active.


How do I get the Compiz settings managers installed and working again?

---

### Post by jollysnowman on 2009-12-19
Mmk, regarding the terminal result: If you have Synaptic (the app) or the System Updater open, you can't run apt-get in the terminal. Close Synaptic, run that command again, and you'll see a different result.

I believe the exact package is "compizconfig-settings-manager"... or some hyphenated version of that lol.

---

### Post by kellemes on 2009-12-19
```
sudo apt-get install compizconfig-settings-manager
```

ccsm is the command to start it.

---

