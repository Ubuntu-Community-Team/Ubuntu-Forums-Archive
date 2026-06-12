---
title: "how do i install Windows having only Ubuntu installed on my machine"
date: 2009-03-09
forum: General Help
---

### Post by sheshdd on 2009-03-09
Hi,i'm currently using Ubuntu 8.10 on my pc and it uses the whole c:\ drive,i wanna know how i can install windows xp and have both OS's working,do i create a ntfs partition from ubuntu and install windows there?

---

### Post by kestrel1 on 2009-03-09
Yes, but I would suggest that you put the Windows partition at the start of the drive.
You will also need to re-install the Grub boot loader on to the MBR, because Windows will overwrite it.
This link should help: [http://onlyubuntu.blogspot.com/2008/06/howto-re-install-grub-after-windows.html](http://onlyubuntu.blogspot.com/2008/06/howto-re-install-grub-after-windows.html)

---

### Post by Woody1987 on 2009-03-09
First of all linux doesnt use letters such as c: to describe partitions and disks. 

You will need to shrink the ubuntu partition using a livecd and running gparted. Once done you should be able to install windows normally on to the freed up space. The only problem with this is that windows will overwrite grub and this will need reinstalling otherwise ubuntu will be inaccessable.

---

### Post by kanikilu on 2009-03-09
See this wiki page: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

The section you want is "4. Installing Windows After Ubuntu".

---

### Post by wsonar on 2009-03-09
> **sheshdd said:**
> Hi,i'm currently using Ubuntu 8.10 on my pc and it uses the whole c:\ drive,i wanna know how i can install windows xp and have both OS's working,do i create a ntfs partition from ubuntu and install windows there?

you have ubuntu installed on your whole c:\drive???? j/k;)

you can use gparted to resize your partition

---

### Post by sheshdd on 2009-03-09
okay,thanks a lot ,i think reading those links should get me going,it's all pretty well explained.

oh and,yeah,i know,no drive letters,what was i thinking

---

