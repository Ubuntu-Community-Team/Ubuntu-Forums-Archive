---
title: "GParted instructions"
date: 2011-04-12
forum: Desktop Environments
---

### Post by Dondermans on 2011-04-12
Hello all,

I have got an external harddrive (1TB) connected to a dual boot system. I formatted the drive using the NTFS filesystem, to be able to use it in Windows XP as well. 

Because I am using Ubuntu far more than Windows *and* because I read that the performance of the drive can be improved by using a EXT4 filesystem instead of NTFS, I would like to create a large EXT4 partition and a smaller NTFS partition. When using GParted I get the following message: 

[IMG]http://i133.photobucket.com/albums/q41/Don82/Publiek/Ubuntuforums/gparted.jpg[/IMG]

I am not quite grasping the instructions. In my mind it states either
- run chkdsk /f /r on Windows, reboot, reboot 

or

- run chkdsk /f /r on Windows, reboot, run chkdsk /f /r on Windows, reboot

I have got two questions:
1. I ran chkdsk /f /r twice, rebooting twice after each run. The same error persists. Can I safely resize NTFS now, using the --bad-sectors operator?
2. Should I replace a 1 TB disk because of eight bad sectors?
3. Is there any way to tell the drive is failing (there does not seem to be S.M.A.R.T. information available in 'System -> Disk Utility')?

Regards,
Don

---

### Post by 3Miro on 2011-04-12
You should reboot the hardriver not windows. To reboot a hraddrive, disconnect and reconnect it (properly).

The error could be due to Linux and Windows both writing to the disk and confusing the software on what is "bad sector". Windows may be able to clean the errors (windows is the better choice here as NTFS is its native format). However, it may be that the HDD is failing.

Once an HDD start failing, it usually fails fast. It may be usable for quite some time, but I wouldn't trust to put anything important on this drive.

---

### Post by Dondermans on 2011-04-12
Thank you. I am running chkdsk /f /r at the moment and will reboot the harddisk twice after that. If all goes well, I suppose GParted should no longer report back errors, but we'll see.

Your remark about using Windows to check a NTFS partition as it is a Windows native filesystem is interesting. Does it also mean that it would be more prudent to resize the NTFS-partition in Windows and add a EXT4-partition in Linux?

Regards,
Don

---

### Post by oldfred on 2011-04-12
chkdsk may take a very long time on a partition that large. If you get errors you need to rerun it until you have no errors.

My rule has been to use Windows tools on windows and Linux tools on Linux. But sometimes I use Linux to repair windows, but never vice-versa.

---

### Post by Wiebelhaus on 2011-04-12
Basically what it's telling you is , it simply didn't shut down clean (ntfs will leave a "dirty flag" if shutdown improperly), You must safely remove or properly shutdown your system. ntfs-utils checks for unclean shutdown because it could possibly damage something if it's writes to the drive , so run chkdsk /f from your windows command line and reboot or remove the drive cleanly.

---

### Post by Dondermans on 2011-04-13
3Miro, oldfred & Wiebelhaus,

Thanks for taking the time to respond to my questions. Once I ran chkdsk /f /r and rebooted the harddrive by removing it safely, the dirty flag does no longer appear in GParted. One would think that rebooting Windows would also reboot the harddrive safely. Alas.

I am marking this thread solved.

Regards,
Don

---

