---
title: "Win 7 + ubuntu ...bootloader??"
date: 2009-05-09
forum: General Help
---

### Post by tanveerahmed2k8 on 2009-05-09
well i multi boot with winxp and ubuntu
fist of all:
I have two hard drives One has Xp and the other one has Ubuntu.
i am going to get win 7 this week, and i dont want grub to go, because without it how would i boot into ubuntu?

How can I reinstall grub as my bootmanager? to start at boot?
second of all i neede some help partition the ext3 file system to ntfs on my 200gb harddrive? and help?

---

### Post by Legace on 2009-05-09
Follow instructions here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by jocheem67 on 2009-05-09
I'd recommend the following...install 7 on the first drive..it'll overwrite the MBR with it's own..
Fire up a live-cd and first use gparted ( it's on the live-cd ) to make your first drive the boot-drive.It probably already is...

Use these commands then in the CLI:

> sudo grub
root (hd0)
setup (hd0)

Here's some reading on it:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


The same links, that's nice..

suc6!

---

