---
title: "[ubuntu 16.10] lvm and unity issues"
date: 2017-06-13
forum: Desktop Environments
---

### Post by Lorek on 2017-06-13
I'm running Ubuntu 16.10 Desktop Fresh Install. Kernel Build #52 iirc.

From a fresh default ubuntu desktop install (with LVM), I disable journaling, resize the filesystem (ext4), then the partition (lvm), then ran e2fs for an integrity check on the resized filesystem and re-enabled journaling (on the root drive from a livecd.). No errors, and upon reboot I was able to login with no issues. There was a slight mouse issue where the cursor would jump across an invisible line on the left side of the screen, but upon a second reboot it was corrected.

I then created a lvm snapshot, made some minor changes and tested the snapshot. Since it is a root drive it doesn't merge the changes until the next reboot. I reboot  have the same issue, reboot again, and log in, and while it will log in, no windows will paint, and the Ctrl+Alt shortcuts for the TTY console are ignored.

There are a number of unity window assertion fails and BAMFd assertion fails (relating to menus) in dmesg. 
Additionally there seems to be a problem with the plymouth grub menu when attempting to boot into recovery mode. (The workstation, it hangs). 

I've no such problems under X11 and CentOS7 but for reasons, Ubuntu is a better choice for my current hardware profile.

I'm hoping someone has some suggestions on how to correct or sidestep this issue.

Edit: No proprietary display drivers were installed that might have caused this. Additionally, it appears that logging out and logging back in somewhat correct it. Though there seems to be a high recurrence rate.

---

### Post by Lorek on 2017-06-14
So it seems this is a known bug with unity, and there doesn't appear to be any fixes. The bug information can be found [here #1532226]("https://bugs.launchpad.net/ubuntu/+source/bamf/+bug/1532226").

---

### Post by mc4man on 2017-06-14
Try 16.04 & see if any better. 16.10 is end of life next month, 17.04 Ubuntu is equally useless. 
(- or try [17.04 Ubuntu-gnome]("https://ubuntugnome.org/download/") as that's where Ubuntu is going anyway..

---

