---
title: "Problem restoring Grub and boot.ini"
date: 2008-12-24
forum: General Help
---

### Post by smarks on 2008-12-24
OK, first off I am pretty familar with ubuntu and I have restored grub before but this time its tricky.

I have 1 sata hdd with ubuntu 8.10. 1 IDE hdd with XP pro. I installed XP and then ubuntu stopped working so I restored grub and got an error 17. I played around with my menu.lst and now ubuntu works but I dont have an option for XP. In my menu.lst it says this below. Please help. I know im really close to figureing this out but I would like some professional help. 

#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro



## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=07f49238-d5af-47ce-a3ad-1f4081f10ffb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=07f49238-d5af-47ce-a3ad-1f4081f10ffb ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

---

### Post by caljohnsmith on 2008-12-24
In order to get a clearer picture of your setup, how about opening a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup, and also help us figure out what Windows entry should work in your menu.lst.

---

