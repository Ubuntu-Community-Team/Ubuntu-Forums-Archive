---
title: "Can't remove old kernels"
date: 2009-03-22
forum: General Help
---

### Post by laloruelas on 2009-03-22
:confused: When ever i try to remove old linux kernels and images synaptic returns a post-trigger error. i don't know how to fix this and i don't have extra space to keep the old ones >:[

---

### Post by zvacet on 2009-03-23
```
sudo apt-get --purge remove package_name
```

---

### Post by laloruelas on 2009-03-26
Doesn't work, returns Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Kevbert on 2009-03-26
What do you get with
```
df -h
```
It may be that one of your drives (possibly /boot) is full.

---

### Post by laloruelas on 2009-03-26
i got the following:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              94G   39G   50G  44% /
tmpfs                1002M     0 1002M   0% /lib/init/rw
varrun               1002M  340K 1002M   1% /var/run
varlock              1002M     0 1002M   0% /var/lock
udev                 1002M  108K 1002M   1% /dev
tmpfs                1002M  160K 1002M   1% /dev/shm
lrm                  1002M  2.0M 1001M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             3.7G  1.2M  3.7G   1% /media/disk-1[/FONT][/FONT]

---

### Post by 16sinker on 2009-03-26
Try alt+f2. Type "gksu gedit /boot/grub/menu.lst" without the guote marks. The file will open, scroll down to the bottom of the file where it says "end default options" where you will find all the menu entries for various kernels. Highlight the ones you don't need-right click and delete.

---

### Post by Kevbert on 2009-03-27
> **16sinker said:**
> Try alt+f2. Type "gksu gedit /boot/grub/menu.lst" without the guote marks. The file will open, scroll down to the bottom of the file where it says "end default options" where you will find all the menu entries for various kernels. Highlight the ones you don't need-right click and delete.

That will only remove the grub entries, it will not remove the obsolete linux kernels.
what you could try is to open terminal and enter
```
cd /boot
ls -l
```
If there are any .bak files you can remove them with
```
sudo rm *.bak
```
Then try opening Synaptic and search for linux-image. Now try a complete removal of the unwanted linux-image...generic files for the kernels you no longer want. It's always best to keep the two most recent kernels (in case of problems). This will automatically remove any obsolete grub entries.

---

### Post by laloruelas on 2009-03-27
> **Kevbert said:**
> That will only remove the grub entries, it will not remove the obsolete linux kernels.
what you could try is to open terminal and enter
```
cd /boot
ls -l
```
If there are any .bak files you can remove them with
```
sudo rm *.bak
```
Then try opening Synaptic and search for linux-image. Now try a complete removal of the unwanted linux-image...generic files for the kernels you no longer want. It's always best to keep the two most recent kernels (in case of problems). This will automatically remove any obsolete grub entries.

it Didn't work :(  returned error exit status 2

---

### Post by Dale61 on 2009-12-12
> **Kevbert said:**
> 
Then try opening Synaptic and search for linux-image. Now try a complete removal of the unwanted linux-image...generic files for the kernels you no longer want. It's always best to keep the two most recent kernels (in case of problems). This will automatically remove any obsolete grub entries.

This last bit was all I needed to do to remove the -14 & -15 kernel.  However, this was AFTER an update to kernel -17, and the now-to-be-expected sh:grub 'greeting' when restarting.

---

