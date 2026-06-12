---
title: "HUGE partition problem: Error 13"
date: 2008-05-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PharmD on 2008-05-30
Okay guys I have two partitions, a Windows XP partition and Ubuntu.  Recently I shut down windows, booted up ubuntu, then later shut it down as well.  Later I came back to start up the windows partition and it is giving me an error 13 and saying I can't start the partition.  Can someone please help, I have very important documents and can't afford to lose them.  Nothing else was changed.  I do have the partition program "something" live burnt onto a CD if that helps but I just have no ideas as to where to go next. 

I did find a thread on this in the forum but they said to check menu.lst and make sure it said hd(0,0) and it does so I am confused.

---

### Post by pastalavista on 2008-05-30
post the menu.list text


(you should be able to see (most of) your windows partitions and access documents on them with Ubuntu)

---

### Post by PharmD on 2008-05-30
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=888c227f-c41b-471a-97b1-a6da9656896f ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=888c227f-c41b-471a-97b1-a6da9656896f ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by jsc1959 on 2008-05-31
here is a description of various grub error messages. Hope this helps.

[http://www.uruk.org/orig-grub/errors.html#stage2](http://www.uruk.org/orig-grub/errors.html#stage2)

---

