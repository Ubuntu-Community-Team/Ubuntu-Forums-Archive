---
title: "Default Disk Mount Info"
date: 2009-01-21
forum: General Help
---

### Post by willid on 2009-01-21
Hi all, bit of a newbie question:

Where does Ubuntu store it's mount information?
e.g. If I click on "Places > My Disk" what mount command gets issued.

I need to know this because I have cobbled together a shell script that checks whether a drive is mounted before launching a program and if not, mount the volume first. Rather than reverse engineer every possible option and switch for mounting said volume I would rather use Ubuntu's choice of options.

Hope that makes sense to someone.
Will

Sceptical of Linux at first but after an initial learning curve I will NOT be returning to WINDOZE and my entire house is now open source! (including XBox, Ipod and PDA)

---

### Post by buzz57 on 2009-01-21
using the mount command from a terminal will show the current state of mounted drives and fdisk -l will give you more information also look at /etc/fstab and you will see what is mounted on boot

---

### Post by drs305 on 2009-01-21
If you are looking for a file for a script to read to obtain currently mounted devices the file to check is **/etc/mtab**

---

