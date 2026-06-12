---
title: "After resize booting become slower"
date: 2009-02-26
forum: General Help
---

### Post by hayig2000 on 2009-02-26
Hi all

i expanded my ubuntu partition and after doing this, boot time has been prolonged by 10 -15 seconds....(and after that fixed grub issue)


is there a way to have the boot time back to normal?

using ubuntu 8.10
having one  hard drive with a separate partition for ubuntu

---

### Post by Herman on 2009-02-26
You could try running your Ubuntu Live CD and opening Gnome Partition Editor. 
Right-click on your Ubuntu partition and select 'check' from the right-click menu.
Click 'confirm', and then 'confirm' again in the confirmation window.
Then wait while GParted runs a file system check in your partition.

Reboot and see if that has improved your boot time.

How often do you need to reboot Ubuntu?
Ubuntu very rarely needs to be rebooted, only when we receive a new kernel in an update.

---

### Post by hayig2000 on 2009-02-27
i checked the ubuntu partition but still the same

and it occurs in the first boot (not in the reboot)

the boot is slowed by the text displayed: booting kernal [ok] ,starting ....[ok]

---

