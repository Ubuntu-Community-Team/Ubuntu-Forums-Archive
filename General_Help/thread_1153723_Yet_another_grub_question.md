---
title: "Yet another grub question"
date: 2009-05-09
forum: General Help
---

### Post by tacomodo on 2009-05-09
First off, I am not being lazy, I just can't seem to find a guide which applies to me. If anyone has one, I would gladly read it :)

My scenario:
I have two harddrives. One has W7 and the other one has Ubuntu.

How can I install grub to let me choose which to start at boot?

Last time, I had W7 installed and booted from the Ubuntu CD and it made the nice grub menus itself, but I would rather not have to reinstall Ubuntu again.

Is there any hope?

---

### Post by Legace on 2009-05-09
So you want to restore GRUB after Windows removed it?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by tanveerahmed2k8 on 2009-05-09
im gona get win 7 aswell so i need to find a way to fix this problem

---

### Post by tacomodo on 2009-05-09
> **Legace said:**
> So you want to restore GRUB after Windows removed it?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
I did:
```
sudo grub
grub> find /boot/grub/stage1
grub> root (hd0,0)
grub> setup (hd0)
```
Rebooted, and absolutely nothing happened...
What exactly did the "find" command do? Did it find stage1 for the Ubuntu boot, or Windows boot? If it was the first, then maybe I need to change the boot order in the BIOS?

---

### Post by tacomodo on 2009-05-09
It seems I answered myself.

Grub must have been installed to the drive that Ubuntu is on so when I changed the boot device priority i my BIOS, everything seems to be back to normal :)

Thanks a lot for the help!

---

