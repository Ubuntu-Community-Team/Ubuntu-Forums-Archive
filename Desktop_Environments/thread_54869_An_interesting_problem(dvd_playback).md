---
title: "An interesting problem(dvd playback)"
date: 2005-08-06
forum: Desktop Environments
---

### Post by petrjanda on 2005-08-06
Xine and other programs report permission denied on /dev/dvd using a non-admin account, but the permissions are correct(777 by default). I keep getting permission denied untill i manually run chmod 777 /dev/dvd. What's the problem? I can mount the disk no problem.

---

### Post by kosmic on 2005-08-06
please do a 

sudo cat /etc/fstab so we can see how the permissions are for your dvd drive,

---

### Post by petrjanda on 2005-08-06
[QUOTE=kosmic]please do a 

sudo cat /etc/fstab so we can see how the permissions are for your dvd drive,[/QUOTE]
The machine is not here, but they  are the defaults everyone else has. I havent touched /etc/fstab. The problem that buffles me is that /dev/dvd has lrwxrwxrwx, thus 777, but I cant play any dvd untill I su and run chmod 777 /dev/dvd manually.

EDIT: Didnt realize /dev/dvd is symlinked to /dev/hdc. Then I see why /dev/dvd has 777 on it and why chmod 777 /dev/dvd solves it. This maybe a group problem, user is in no group, which group does ubuntu require to run dvds?

---

### Post by petrjanda on 2005-08-07
Doesn't anyone know which group I must put users in so they get permission to open /dev/hdc?

---

