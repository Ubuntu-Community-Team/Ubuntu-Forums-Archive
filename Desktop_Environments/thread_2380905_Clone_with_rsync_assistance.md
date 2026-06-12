---
title: "Clone with rsync assistance"
date: 2017-12-23
forum: Desktop Environments
---

### Post by Geoff_Lane on 2017-12-23
Folks,

I am running 16:04 and would like to copy system onto another disk.

That is not a problem, can use dd from the terminal but want to enquire;

If I install a fresh copy of 16:04 then use rsync to copy contents from old disk to new disk would this work?

Assume also that when using rsync then source and destination can't be the actual OS at the time due to system files.

Geffers

---

### Post by speartip on 2017-12-23
If you're cloning from one disk to another then Clonezilla or fsarchiver, would be your best bet.
If you're installing a fresh system on to your new disk, and just want all your personal data moving across then rsync would be best.

---

### Post by oldfred on 2017-12-23
I prefer new install and rsync your data only, not system. Usually /home. If you have server configuration with web, database or other, you would need to copy those, also.

I have almost all my data in /mnt/data separate partition and back that up, but mount in every install on every drive. And then copy it to my other system using flash drives that then also serve as backups.
Only if you have made some system config file changes may you want to backup /etc. I only change several files, fstab, 40_custom, and exports, so I manually copy them into /home so my normal backup of /home has them and I can copy back if needed.

You cannot keep a cloned disk mounted as it has same UUIDs and then when you reboot you may not be using system you think you are using. It depends on UEFI/BIOS on which drive is seen first.

---

### Post by sudodus on 2017-12-23
> **Geoff_Lane said:**
> If I install a fresh copy of 16:04 then use rsync to copy contents from old disk to new disk would this work?

General answer: **rsync** can provide only part of the solution.

Copy the content of the root partition (and other partitions with file systems if any) with rsync.

If your system boots in BIOS mode (alias CSM alias legacy mode), you must also install the bootloader to the head of the drive

If your system boots in UEFI mode, the system boots via the EFI system partition, and its content can be copied with rsync.

You would probably also want to create a swap partition.

Finally you need to match the UUIDs of the partition(s) with what is specified in the files **/etc/fstab** and **/boot/grub/grub.cfg**
> 
Assume also that when using rsync then source and destination can't be the actual OS at the time due to system files.


That's right, if you use the file system **ext4** (the standard file system of Ubuntu), you should boot from another drive to avoid that system files are modified during the copying process.

[hr][/hr]
I think cloning with Clonezilla is much easier. [http://clonezilla.org](http://clonezilla.org)

Or, as suggested by oldfred, make a fresh installation and copy your personal files from the old system to the new system.

---

### Post by Geoff_Lane on 2017-12-24
> **sudodus said:**
> General answer: **rsync** can provide only part of the solution.


Or, as suggested by oldfred, make a fresh installation and copy your personal files from the old system to the new system.

Clean installs are usually the best, I'll probably go for that.

Geffers

---

### Post by Geoff_Lane on 2017-12-24
Thanks for advice folks.

Geffers

---

### Post by sudodus on 2017-12-24
Good luck with your new system, and when your problems are solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---

