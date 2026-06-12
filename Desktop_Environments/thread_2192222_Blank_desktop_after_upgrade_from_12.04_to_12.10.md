---
title: "Blank desktop after upgrade from 12.04 to 12.10"
date: 2013-12-06
forum: Desktop Environments
---

### Post by msinfo on 2013-12-06
Hello,

My system: 32 bit, PIV 2.4 Ghz, 1GB RAM, No Graphic Card, Windows / Ubuntu dual boot system.

Two days ago, I did upgrade, which went smoothly. After restarting system, and doing login, I see only blank desktop, no Unity launcher or task bar, no gui, nothing. I can press Ctrl+Alt+T and open programs, but graphics looks very old.

I was trying solutions posted on this forums, one of command 
sudo apt-get install -f gave following error, which I was getting previously also.

Below error: 
```
Preconfiguring packages . . .
dpkg: error: parsing file '/var/lib/dpkg/available' near line 59
missing package name

A fatal error occurred.
Please report this as a bug and include the files.
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in your report. The upgrade has aborted.
Your original sources list was saved in 
/etc/apt/sources list.distUpgrade

System Error E: sub-process /usr/bin/dpkg/ returned an error code (2)
```

---

### Post by fantab on 2013-12-09
You have a damaged */var/lib/dpkg/available*, you have to erase the file and rebuild it... and along with lets also do some apt cleaning:

Try this:
```
sudo dpkg --clear-avail
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update && sudo apt-get dist-upgrade
```

And Reboot. Tell us how it goes.

---

### Post by msinfo on 2013-12-11
Thanks, yeah, what you said, worked. DPKG was really broken.

---

