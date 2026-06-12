---
title: "Two basic questions in Ubuntu"
date: 2006-10-01
forum: Desktop Environments
---

### Post by ss0007 on 2006-10-01
Hi ,
1) I have installed Dapper for my new external hard  disk. I have the device shown in /dev as sda7 . So i  changed the grub settting to .

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

I wonder why "root (hd0,6)" only works. If i set to "(sd0, 6)" the grub reports " error parsing the line " . 
Will thr  be any problem in continuing with hd0,6 although my root parttion is setup in sda7 ??

2) In setting the repo's in my sources.list of apt-get , is thr any need to have "deb-src ... " line . I mean i dont compile any packages , i just need the apt to install. 

Thanks .

---

### Post by Cable on 2006-10-01
Just comment out the deb-src lines in your sources.list.  Those are just for source code, which obviously you don't really need.  It'll help conserve some space in the long run.

---

