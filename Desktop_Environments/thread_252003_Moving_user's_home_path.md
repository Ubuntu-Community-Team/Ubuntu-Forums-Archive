---
title: "Moving user's home path"
date: 2006-09-06
forum: Desktop Environments
---

### Post by Gleams on 2006-09-06
Hi
I installed Ubuntu on a 6Gig hdd i had laying around and now that i have decided i want to keep it, i want to move the user's home directory to a larger 120Gig hdd as several people recommend having it on a different partition. Is the moving of a user's home directory relatively straight forward?

---

### Post by ayoli on 2006-09-06
create a partition on your 120GB hd, copy your user(s) folders on it (not home, only subdirs named as users).
then edit your fstab:
```
sudo gedit /etc/fstab
```
add a line such as:
```
/dev/hda3       /home           ext3    defaults        0       2
```
replace hda3 with the partition number of your disk.
then reboot.
if you did the copy as root you 'll have to:
```
sudo chown -R username.usergroup /home/username
```
regards.

---

