---
title: "ubuntu 18.04 on Dell XPS-13-9370 does not &quot;see&quot; usb external disks"
date: 2020-06-13
forum: Desktop Environments
---

### Post by Gingalone on 2020-06-13
My laptop very often (not always) does not "see" a connected usb disk (active and rotating! File sys Ext4) no way to mount it since for the system it does not exist. VERY annoying!
```
sudo fdisk -l
``` does not show the external disk. I keep detaching and reconnecting several times the disk and sometimes at last it is "seen" and mounted but often there is no way. I try rebooting the laptop but sometimes even this radical "cure" does not make the external disk seen and mounted. 
Thank you for any help

---

### Post by CelticWarrior on 2020-06-13
I would start by updating UEFI.
And being a current model, why 18.04? Ubuntu 20.04 should work better with that hardware.

---

### Post by oldfred on 2020-06-14
USB ports may not have enough power for spinning external drives. Do you have separate power source or are using USB only? 
I have a SATA to USB adapter and SSD works great and HDD does not even come up.

---

### Post by Gingalone on 2020-06-15
Thank you for reply!
My USB disk (3 TB) has not external power inlet and when connected it always spins. At my usual work place (I am presently working from home due to epidemic) I got a dock station which is powered but even there sometimes the usb disk is not "seen". Never tried with SSD usb disks.
PS: I updated the UEFI not later than 3 or 4 months ago.
I stick to Ubuntu 18.04 (preinstalled by Dell) because I know for personal experience that upgrading Ubuntu is never painless. I learned to keep the LTS versions until their dismission, then I do a clean install of the latest LTS (with all software, network, printers ecc. ecc. to reinstall, at least 2 days work).

---

### Post by oldfred on 2020-06-15
I understand with Dell and pre-installed Ubuntu.
The few that have posted a Boot-Repair summary report for pre-installed Dell seem to have a customized grub.cfg and has an extra boot stanza to boot the recovery mode which is an Ubuntu image. 
Not sure if it is directly booting an ISO with grub's loopmount or not,  which is what I do to install.

I install every version and have a another install of current version in case I want to test something but not change my working install. But then I scripted most of the reconfiguration changes I want.
Install takes about 10 min to SSD from HDD, script to set up links to data and some configuration is instant. Script to install my favorite apps is 20 min but I sometimes just reinstall everything & that is a bit longer.

If you have good backups, it should not take more than an hour or two to restore system by reinstalling & restoring the backups of your data. Your configurations are all in /home, you may have changed some system configurations in /etc.

---

### Post by Gingalone on 2020-06-17
Thank you oldfred, to me (Ubuntu user for about 10 years, but far far away from your level of Linux expertise!) your installation times look a bit optimistic...
Anyway, I'll think about!

---

### Post by Autodave on 2020-06-17
Gotta start with a  *good *powered USB adapter.

---

