---
title: "Moving Ubuntu to bigger hard drive"
date: 2005-10-13
forum: Desktop Environments
---

### Post by caeserjk on 2005-10-13
What is the best solution to move a running ubuntu system off of a completly full hard drive to a bigger hard drive. Please note it is a ubuntu only system, meaning that there are no other partitions other than what ubuntu automatically setup. I also need the mbr to be initialized on the new drive also. Looking to just be able to swap.

---

### Post by Velox Letum on 2005-10-13
What I did was plug in the new drive along with the old drive, boot into my system, reformat/make filesystem on the new drive, mount it, and copy over all the files. Once they're all copied over, edit /etc/fstab to make the new drive the correct mount point (ie, /) and change the old drive's mount point, reboot, and it should boot...though GRUB might be a problem. In that case you'd reinstall GRUB [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows") (article that should help) onto the new drive.

---

