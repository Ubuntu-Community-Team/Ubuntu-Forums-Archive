---
title: "Root and EFI mounts show on Dock (Launcher) ?"
date: 2021-09-15
forum: Desktop Environments
---

### Post by captclearleft2 on 2021-09-15
Hello great community of Ubuntu,

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289172&stc=1[/IMG]

I have two mounts that show up after boot (root, and efi).  They appeared after an update and installation of rtl-sdr software.
NOTE: I do not have to enter username or password upon boot.  
NOTE: I had to use "Sudo Nautilus" to get RTL-SDR software installed.   

These mounts go away if I log out, and log back in - When I log back in, I have to use my user password.

Why is this happening.?  What is a method of fixing this?

Thank You so much...

---

### Post by grahammechanical on 2021-09-15
If, at the time we install Ubuntu we set the OS for automatic login it is then normal not need to enter username & password when we boot. It is also normal to have to enter the password when we logout and log back in.

What is rtl-sdr software? What did you do to get Nautilus to install the rtl-sdr software. I did not think that it was possible to use a file manager to install software. Perhaps this was software that is not available from the Ubuntu software repositories. Did you use the file manager and double clicked a file and then the file installed the software? The two images shown are not the standard Ubuntu 20.04 image icons for a mounted partition.

Please explain the process by which you installed this software and where you obtained the software from. I think it is more likely that the installation of this software is causing this to happen rather than the update/upgrade process.

Regards

---

### Post by captclearleft2 on 2021-09-17
Thank You [[COLOR=#000000]@grahammechanical[/COLOR]]("https://ubuntuforums.org/member.php?u=1087323") 	 .  

This issue associated with this thread is: **The mounted drive icons that are in the dock (in the image, bottom left). **Those icons should not appear after boot.

The other details about login and logout... ... are just notes to help diagnose why this happening.  

Nautilus was used to create a folder and a file while installing software.  I had to launch Nautilus using the Terminal (sudo nautilus) to enable write permissions to create a folder and file to allow the software somewhere to store log files...  I believe I had to do this because I have autologin enabled with ubuntu upon boot, and my user does not permissions.  I believe that after I did this - now, every time it boots - It has those drive icons mounted in the dock (root, and efi).

I am trying to figure out, why did this happen, and how to correct. ??

Thanks so much

---

### Post by The Cog on 2021-09-17
You might be able to make them go away by making an entry for them in fstab. I hide some partitions from my desktop that way, configure them for noauto so they don't actually mount. But having an fstab entry for them seems to stop the desktop thinking they're removable and showing icons for them. I use a line like this, you just have to get the device ID right.
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/nvme0n1p3  /mnt/nvme0n1p3   auto    noauto         0       0
```

---

### Post by miangmbn on 2022-07-03
I has this problem when I reboot with a DVD in drive, which was cracked and not quite readable , when I removed it and reboot the problem disappeared

---

