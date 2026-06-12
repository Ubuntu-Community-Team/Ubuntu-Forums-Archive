---
title: "Subfolder Permissions"
date: 2009-01-15
forum: General Help
---

### Post by LetThereBeNick on 2009-01-15
I recently partitioned my HD into four sectors: an ubuntu section (~20GB, ext3), a Windows 7 BETA section (~20 GB, NTFS), a swap section, and a "Media" section to be accessible from both operating systems(~950GB, NTFS). 
The media drive is set to mount at "/windows" and I set my account's Home folder to "/windows/Nick" and another user's Home folder to "/windows/user2".
Now here's the problem. I want to allow user2 to access their folder on the /windows mount, but not my Home folder. I tried changing permissions for "/windows/Nick" so that only I could access it, but the settings immediately revert back to the drive permissions specified in /etc/fstab. I can change the permissions for the entire drive, but it seems the only way to allow user2 into the drive is to also allow them into my personal Home folder.

Am I doomed to keep doubles of all my files on seperate partitions, or can this bug be worked out?

---

### Post by mag_dex on 2009-01-15
Windows partitions don't work with Linux permissions. 
It's not Linux type of format. 
You can't change permissions to files from windows disks by chmod and so on.

I'm not so sure, but I think I'm right :)

---

