---
title: "ubuntu hard drive partition problems"
date: 2009-01-27
forum: General Help
---

### Post by banana jama on 2009-01-27
today there was a problem with ubuntu which caused me to install a second ubuntu. this second ubuntu has a partition of 40gb and the first 200gb. i transfered all the data i needed from the first ubuntu to the second one and formatted the partition of the first (or so i thought). since then i cannot you the 200gb partition and there is a file called lost+found which i cannot access. further more when i ran gparted it says that this partition is used for boot and that only a "superuser" has permission. how can i gained access to this partion? if this partition is used the boot how can i make the 2nd partition the one responsible for this. also there are now 2 swap drives what happens if i delete the one that belonged to the 1st(200gb partition) ubuntu? 
         any suggestions will be helpful

---

### Post by oldos2er on 2009-01-27
Can you please post the output of
```
sudo fdisk -l
```
?

---

### Post by icheyne on 2009-01-27
Can you rescue the data with a live CD,  copy it to an external drive and reinstall?

---

### Post by banana jama on 2009-01-27
here is the out put from the command you gave me oldos2er

```
akeem@akeem-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29498de2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24407   196049196   83  Linux
/dev/sda2           24408       30401    48146805    5  Extended
/dev/sda5           29694       30401     5686978+  82  Linux swap / Solaris
/dev/sda6           24408       29471    40676517   83  Linux
/dev/sda7           29472       29693     1783183+  82  Linux swap / Solaris

Partition table entries are not in disk order
akeem@akeem-laptop:~$ 


```

to icheyne : i really do not want to reinstall.

---

### Post by banana jama on 2009-01-27
bump

      i've found that if i run the code sudo nautilus i can use the partion but i don't want to do this everytime. also i would like to delete the lost + found folder but am afraid that the boot loader is in this folder and will not be able to use ubuntu. is there any way of finding if grub is in that folder and giving permission to everyone (not just sudo nautilus)?

---

### Post by banana jama on 2009-01-27
i think i solved my problem to future people with the same problem who stumble upon this thread you can do this:

```
sudo nautilus
```
    this gives you root access

then go to your partition and right click----> properties----> permission and where you see root click on it and scroll to your name(or what every you name your account) this will give you permission. if you have a lost + found folder right click on it and do the same as the partition. it doesn't contain any grub info its empty. 

solved

---

