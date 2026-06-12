---
title: "INSTALLING  UBUNTU8.10  alongside with FEDORA 10"
date: 2009-02-20
forum: Desktop Environments
---

### Post by rahul_supersaiyan on 2009-02-20
Hi all,
     I am having a small problem.
      I already have installed fedora 10 and now  planned to install ubuntu 8.10.I tried to install from a cd(DESKTOP edition).But since i already have grub in a dedicated partition i did not install it.When i rebooted it is not showing the ubuntu in grub.I edited menu.list by putting the kernal and initrd paths now im getting GRUB:ERROR 1  which says:give absolute path or path of block node device.I have given paths relative to /boot ...here is the part of grub.conf.
I have ubuntu(files) installed in separate partition 14.4gb different from fedora.I have 2 other partitions disk1 and disk2
The names of the partitons given  when mounted automatically when in fedora are ...
disk    disk-1     disk-2
Problem is that the names disk  disk-1  and  disk-2 keep changing among themselves each time when i boot fedora so i dont know what to keep in grub.conf
[B]title Fedora (2.6.27.5-117.fc10.x86_64)
	root (hd0,7)
	kernel /vmlinuz-2.6.27.5-117.fc10.x86_64 ro root=UUID=b48471ab-4533-4f19-9020-3149c6ae2dbc rhgb quiet
	initrd /initrd-2.6.27.5-117.fc10.x86_64.img
title ubuntu
	root (hd0,5)
	kernel ../media/disk-2/boot/vmlinuz-2.6.27-7-generic
	initrd ../media/disk-2/boot/initrd.img-2.6.27-7-generic
	chainloader +1[/B]

---

