---
title: "X-window fails to start"
date: 2006-08-07
forum: Desktop Environments
---

### Post by satimis on 2006-08-07
Hi folks,

Ubuntu-6.06-amd64

After running "sudo apt-get upgrade" X windows/Gnome desktop fails to start.  On login screen typing User_name and password it prompts a black screen, hanging there for prolonged time.

Pls advise which file I have to check.  TIA

B.R.
satimis

---

### Post by bmonkey on 2006-08-07
Sounds like your xorg.conf is broken :/

try login just using the console (shell) watever u wanna call it.. then cd /etc/X11/

then do a ls and check to see if maybe it backed up ur xorg.conf (to like xorg.conf.backup , or a date) 

Then just replace the backup over the xorg.conf and it should work
Try this if u have no idea what to do...
```

cd /etc/X11

```
then
```

grep xorg.conf*

```
this will show u all xorg.conf files and different names. Try look for something like xorg.conf_backup_200608011843 where the numbers indicate the year, month,day and time - try find the latest

then
```

sudo cp xorg.conf.your.chosen.backup xorg.conf

```
that will replace the xorg.conf with the backup.. then restart x server or just reboot

p.s maybe make a backup of the original xorg.conf before u try anything..
the command is

```

sudo cp xorg.conf xorg.conf_my_backup

```
Do that in the /etc/X11/ directory

---

### Post by satimis on 2006-08-07
Hi bmonkey,

Tks for your advice.

$ sudo ls -al /etc/x11 | grep xorg.conf*

only found xorg.conf

$ sudo find / -name xorg.conf*```

/var/lib/x11/xorg.conf.md5sum
/var/lib/x11/xorg.conf.roster
/etc/X11/xorg.conf
/usr/share/man/man5/xorg.conf.5x.gz
/usr/share/xresprobe/xorf.conf
/usr/share/ubuntu-docs/ubuntudesktopguide/sample/xorg.conf_disablectrlaltbackspaccegnoem

```

No backup file found.

B.R.
satimis

---

