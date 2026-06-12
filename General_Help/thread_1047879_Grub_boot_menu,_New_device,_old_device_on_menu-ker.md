---
title: "Grub boot menu, New device, old device on menu-kernel Panic"
date: 2009-01-22
forum: General Help
---

### Post by carl99fan on 2009-01-22
I have placed a secondary HDD in my computer with 8.10 on it.
I have remove me old secondary HDD.
My grub boot menus shows the "old" HDD I need to update my menu to the new device. 
ALSO when I boot up from the 8.10 it does not load and I have a Kernel Panic.

it says: /bin/sh: can't open splash
[   11.266424] kernel panic - not syncing: Attempted to kill init!

---

### Post by Crafty Kisses on 2009-01-22
First make sure you have all these config flags enabled in your kernel:
```
CONFIG_NFS_FS
CONFIG_ROOT_NFS
CONFIG_NET_ETHERNET
CONFIG_IP_PNP
CONFIG_IP_PNP_BOOTP

```
I'd also like to see the results of this command:
```
ls -la /boot
```
It possibly could be the Raid drivers too, since you updated, but it could be a number of possible things to be honest. If worst comes to worst, you could always roll back your kernel, not sure what kernel you are using now, but I want to take a look at that as well, so can you also give me the results of this command?
```
uname -r
```

---

### Post by carl99fan on 2009-01-22
I wish I could but It does not even give me a prompt.
I had this 60gbhard drive in another computer as a main hard drive.
I have placed it in this computer and it fails to get past the Ubuntu startup screen.

I can access the 60gbdrive using the 250gbdrive I am on now. I can transfer files and everything.

I tried loading from the earlier kernels in the grub menu but I get the same result.

kernel panic - not syncing: Attempted to kill init!

This 60gb hard drive was set up an a 
HP with amd 3200XP processor and a nvida GeForce 4 card.
it is now in a HP amd X2 4200+ dual core.
I have done similar hard drive swaps such as this without any problems usually just need to install graphics drivers.

Should I try th 60gb in the older unit? maybe then I can get you the info you requested.

---

### Post by carl99fan on 2009-01-22
I LIED! I can NOT transfer files.

The 60gb hard drive is MISSING THE HOME FOLDER!!

---

