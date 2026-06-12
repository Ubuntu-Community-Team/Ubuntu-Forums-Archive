---
title: "Moving ubuntu from one computer to another computer"
date: 2010-02-16
forum: Desktop Environments
---

### Post by carfield on 2010-02-16
Plan to upgrade the computer, is that any tool help? Or I can just copy all file and run "grub-install"??

---

### Post by warp99 on 2010-02-17
Just take the hard drive out of the first computer and move it to the second one, then boot to that drive. Only caveat is if the new computer has a different brand chipset for the video card and you're using the proprietary drivers, ATI or nVidia, setup the new card on your old computer, power down, and then move the drive.

Once you do this if you want to transfer the files to a newer drive boot to a Ubuntu LiveCD or USB and copy all partitions using gparted and reinstall grub. You could also copy the files, but you need to use the command " cp -a" since we need to retain the permission structure and copy directories/files recursively, which the -a parameter does. In either case use a Ubuntu LiveCD or USB so you don't get any errors while copying the files.

Edit: If you just copy the files you have to update the UUIDs for the new partitions on the new drive in the /etc/fstab file.

---

### Post by carfield on 2010-02-18
Thanks a lot , this information is useful

---

