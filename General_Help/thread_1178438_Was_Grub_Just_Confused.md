---
title: "Was Grub Just Confused?"
date: 2009-06-04
forum: General Help
---

### Post by killshot on 2009-06-04
I did something stupid and pulled out a thumb drive without dismounting it.
My screen went black so I rebooted.
When grub started to load it would tell me inconsistent file structure and sometimes it would say something about more cylinders than bios allows.  And then it would give me a prompt with a limited number of commands available.

Booted with a live cd.
I have 2 hard drives.  /sda with Ubuntu and the swap file and /sdb with all my files.
/sdb would mount just fine.  
/sda would not mount and after digging around it tells me that I have a bad superblock.  I tried to load a backup superblock and it did not work.
Everyone I know tells me the drive is screwed, everything I see on google suggested the same.

But then I wondered.  If the drive is so bad and can not mount, then why was grub loading?

So I unplugged /sdb and rebooted.
Everything booted just fine 
Plugged /sdb back in.. rebooted.. everything still fine.

Does anyone have any suggestions on what actually went wrong?

Thanks!

---

### Post by ajgreeny on 2009-06-04
Did the machine run an fsck check at one of the startups?  If so it may have found whatever was wrong with the filesystem and corrected it.  Otherwise I have not got the faintest idea how it managed to fix itself.

---

### Post by VMC on 2009-06-04
If you can get to the recovery boot do an fsck on the partition in question, otherwise do it from the livecd.

Was Ubuntu on the flash drive or was that just another mounted drive?

From livecd output the following:

```
sudo fdisk -l
```

---

