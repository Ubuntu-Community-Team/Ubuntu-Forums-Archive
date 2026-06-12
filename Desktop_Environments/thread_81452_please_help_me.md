---
title: "please help me"
date: 2005-10-24
forum: Desktop Environments
---

### Post by darxburn on 2005-10-24
I can't access my hard drive. I installed Linux Kubuntu, and I have Windows XP, and I can't access my hard drive gest on I instal kubuntu

**Edit:** I tried my best to translate this into English, but I don't know what that last part about *gest* means. --aysiu

---

### Post by paddyg on 2005-10-24
please can you give some more details?

---

### Post by az on 2005-10-24
If you can upgrade to Breezy, there is an easy tool for accessing unmounted disks.

The problem is you installed Ubuntu, but you are not mounting your Windows partition.  You need to edit your fstab file (/etc/fstab) to let your system know that you want to access that disk or partition.

The disks-admin tool in Breezy (installed by default) allows you access your other disks or partitions, so that you do not have to modify the file by hand.

---

