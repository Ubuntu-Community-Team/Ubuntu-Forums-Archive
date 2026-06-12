---
title: "QEMU with winxp"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Justin Holt on 2006-06-20
i found a post on digg that showed how to use win xp in ubuntu, only problem is that i wonder if you can help me, here is the post [http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html](http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html).  But i get that it can't open the cd image from the cd drive, if anyone knows please lemme know.

---

### Post by scxtt on 2006-06-20
can you supply the error (and maybe what step from the article you're doing before you get the error)? ...

i tried Qemu a few weeks ago, it was alright - i think i stopped using it because it  was having trouble reading my XP disk {VMware server had some problems too, but the install didn't 'time out' as it was doing w/ Qemu} ...

edit: i got the 'you're just unlucky' error:> If you get an error Error code 0x800703e6 on Product Activation, then your XP is pre sp1 or sp2, follow these instructions....

---

### Post by lamego on 2006-06-21
The performance with QEMU is really bad. I advise you to use vmware player, it is not open source but it is free and available on the Ubuntu repos.

For more information on how to use vmware player:
[https://help.ubuntu.com/community/VmwarePlayer](https://help.ubuntu.com/community/VmwarePlayer)

---

### Post by Justin Holt on 2006-06-21
I was following the step where you have to first boot the cd  to install
code : 
qemu -boot d -hda winxp.img -cdrom /dev/cdrom -m 256 -localtime

...i get the error
could not open hard disk image 'winxp.img'

and i just want to try this out before i try vmware player...and i don't know how to create a virtual machine for vmware player...

---

### Post by dignome on 2006-06-21
Make sure the disk image winxp.img exists and is valid.  An example for creating a disk is as follows:

qemu-img create -f raw winxp.img 5G

That will create a raw image 5GiB in size.  You can then check its validity with qemu-img info winxp.img

@lamego

qemu w/kqemu and full virtualization is not that slow for Windows NT guests.  Windows XP used to run very slow in qemu until full virtualization was introduced.

---

