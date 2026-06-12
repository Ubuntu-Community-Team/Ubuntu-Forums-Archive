---
title: "Second Hard drive not auto mounting"
date: 2014-07-12
forum: Desktop Environments
---

### Post by wingrider78 on 2014-07-12
Fresh install of 14.04.  Everything was fine, then I "unlocked from launcher" my backup drive.  I didn't need the drive icon showing in the launcher so I unlocked it.  Now it won't automount when the system is restarted.  I can open it from nautilus and it will stay mounted until a reboot.  The options in "disks" shows that it should automount on startup, but it doesn't.  I have the drive showing up in the launcher again, but it still isn't automounting.  It is, however, in the blacklist when I type

```
sudo blkid -o list
```

I never told ubuntu to blacklist this drive, unless it happened when I unlocked from launcher.  Is there a command that will un-blacklist this drive to hopefully get it to automount again?

My end goal is to have the drive automount so it will actually do the nightly backup, but to not have it shown in the launcher.  Thanks in advance for the help...

---

### Post by deadflowr on 2014-07-12
Are you sure the drive was ever automounted in the first place?
There has been a bug(or maybe not a bug) that had unity add the external partitions and other media to the launcher, regardless if they were mounted or not.

Did you add the drives to [fstab]("https://help.ubuntu.com/community/Fstab"), or create a [startup application to automount]("https://help.ubuntu.com/community/AutomaticallyMountPartitions#Per-User_Mounts") them?

---

### Post by wingrider78 on 2014-07-12
I am only assuming it was automounted from the start...since my backups have been happening nightly since I installed 14.04.  Although, I had opened the backup drive up, so maybe that mounted it for me and it wasn't necessarily automounted...

Since the settings in "disks" shows that it should "mount on startup" and "show in user interface", shouldn't it automount?

To answer your other questions, no, I did not add the drive to fstab or create a startup app.  I will look into those links you provided.  Thank you.

---

### Post by wingrider78 on 2014-07-13
I added the drive to fstab and it is now automounting.  Thanks.

---

