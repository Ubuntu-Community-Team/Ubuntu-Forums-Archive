---
title: "LXQT Can't Mount &quot;File&quot; Problem"
date: 2021-09-26
forum: Desktop Environments
---

### Post by mosscomes on 2021-09-26
I have an Ubuntu Samba server running 20.04.3, which has worked well for me for many years. Because there are some functions that I prefer to use a gui, I have installed LXQT 0.14.1 as a lightweight desktop. I meets my needs except for one annoyance. I can not access three of my four internal drives, which are the Samba shares. When I select the drive in the file manager, I get this message: "Can't Mount file."

Now after trying to update LXQT, one of my four samba drives has appeared under devices. I can also access this under computer in the file manager. I have always been able to access external usb drives. The log in credentials are the same. How do I get the other three to show up and be accessed?

---

### Post by GhX6GZMB on 2021-09-26
There's some misunderstanding here. PCManFM-Qt, which is the Lubuntu _file manager_ is not there to do disk management.
Your disks are mounted somewhere in your file system, finding out where is done by using the terminal command lsblk.

_Then_ you can use the file manager to visit the directories where the disks are mounted.

---

### Post by guiverc on 2021-09-26
I always `mount` (or at least ready the mount and use the `noauto` option) via the *file-system table* (`/etc/fstab`) entry; then I find it easier to deal with, but I'd also not perform mounts (*of network shared devices*) via `pcmanfm-qt`.

`pcmanfm-qt` will mount *local* devices (USB drives etc)


*The aim of LXQt is in the first letter; ie. being **light***. * Adding extra non-essential functionality works against the light purpose - so unless it's a necessary feature needed by most users, it won't usually be added (esp. where outside of the intentions of the program)*

---

### Post by mosscomes on 2021-09-26
Maybe I am confused. I am not trying to do disk management with PCManFM-Qt. I am just trying to see what's in the folders, as I can do with external usb drives. Earlier today, one of the drives mounted, but when I rebooted, it disappeared. 

Using lsblk, the four drives mount point is /samba/drivename. The external drive is mounted under /media.

But, you give me a clue. I installed Nautilus under LXQT. Added the other drives from the other locations, and now they show up in both PCManFM-Qt and Nautilus. Not sure how that fixed the problem. Now we will see what happens when I reboot.

---

### Post by guiverc on 2021-09-26
The `mount` itself needs to be done, before `pcmanfm-qt` will use it (the mount function is disk management)

In your final paragraph, it sounds like you used `nautilus` to perform the `mount`, which then allowed `pcmanfm-qt` to use it.  `pcmanfm-qt` will only mount local drives

---

