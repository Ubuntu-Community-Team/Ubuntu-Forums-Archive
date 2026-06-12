---
title: "ebox(Zentyal) bug - if you need it gone!"
date: 2012-03-16
forum: Desktop Environments
---

### Post by youngunix on 2012-03-16
Story short: like most, I installed ebox from U.S.C to try it, it was ok! So, I uninstalled from U.S.C, and later root mail started getting mass mail from "cron" like the following: 
```
/usr/share/ebox-usersandgroups/slave-sync
```

Solutions that **DID NOT **work for me: source [http://ubuntuforums.org/showthread.php?t=1533660](http://ubuntuforums.org/showthread.php?t=1533660)
```
sudo apt-get -V purge ebox
```
and
```
sudo update-rc.d -f ebox remove
```

Solution that **DID **work:
I opened "**File System**", clicked on "**Search**" and typed "**ebox**".
I carefully made sure and deleted (using **BleachBit**) any folders and files that belonged to ebox.
Rebooted, to see if I did mess up the system or fix the problem.
And magically, the flooding stopped.

youngunix,

---

