---
title: "Adding windows 7 to grub along with xp and ubuntu."
date: 2009-03-27
forum: General Help
---

### Post by kodos84 on 2009-03-27
Hey guys, 
I have a machine with xp on it.
I created a new partition with gparted and put ubuntu on it.
Then i decided to try out windows 7 beta. 
I shrunk(sp?) the xp and ubuntu partitions and created a new partition between the two and put windows 7 on it.


I knew installing it would make grub not work but i didn't really mind and I figured i could find a way to restore it. Right now i can boot into windows 7 and xp, but not ubuntu.

So right now I have xp at sda1, ubuntu at sda3 and windows 7 at sda2
I attached the contents of menu.lst

I would really appreciate it if someone could tell me exactly how i can restore grub so i can boot into ubuntu. Thank you.

---

### Post by James_Lochhead on 2009-03-27
Try this [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

It requires a live cd and takes about 5 minutes. It is the normal way to restore grub after you install windows.

---

### Post by kodos84 on 2009-03-27
Thank you! That was just what I needed. 
A little bit of a problem though 
both 
find /boot/grub/stage1
and 
find /grub/stage1
return a error 15: file not found.

---

