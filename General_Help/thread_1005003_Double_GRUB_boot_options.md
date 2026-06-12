---
title: "Double GRUB boot options"
date: 2008-12-07
forum: General Help
---

### Post by arashiko28 on 2008-12-07
I have installed Vista and Ubuntu and from a few days ago, the GRUB menu shows the next, (this is my GRUB menu.lst entry):
> 
title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2b5de95e-da4c-49bf-8282-0d363c65d74a ro quiet splash xforcevesa 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=2b5de95e-da4c-49bf-8282-0d363c65d74a ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2b5de95e-da4c-49bf-8282-0d363c65d74a ro quiet splash xforcevesa 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=2b5de95e-da4c-49bf-8282-0d363c65d74a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1


2 Ubuntu boot options, 2 recovery mode options, 1 memtest option and 2 vista options, it is safe just to simply remove the extra options?:confused:

---

### Post by falcon61102 on 2008-12-07
You should be able to comment out the unneeded boot options without causing any harm to things.  However, it is recommended that you keep one extra boot option for Ubuntu.  If you look closely to your menu.lst you will see that the first two are for the 2.6.27-9 kernal and the next two are for the 2.6.27-7 kernal.  Keeping that extra kernal option will allow you to boot up your system in the event of error or crash to the newer kernal.

---

### Post by brandon90c on 2008-12-07
You could do that, but a better way would be removing the old kernel:
```

sudo apt-get remove linux-image-2.6.27-7-generic

```

---

### Post by geirha on 2008-12-07
Yes, if the newest kernel works satisfactory, then its safe to remove the older kernel entries. Also seems it has found windows vista on two different partitions. If only one of them works, remove the other.

The kernel entries you remove will reappear later though, because whenever a kernel is installed or removed, all ubuntu entries are removed, and then a normal and recovery option is added again for each kernel installed on the system. So to really get the entries gone, remove the kernel package. In your case, removing **linux-image-2.6.27-7-generic** will remove the two previous kernel entries. 

I do recommend keeping two kernels around. A new kernel may introduce some bug that may make your system unable to boot or something, and in such cases it is good to be able to boot the previous kernel.

---

### Post by theozzlives on 2008-12-07
I agree with falcon61102. Comment out the extra Vista and keep the backup kernel.

---

### Post by brandon90c on 2008-12-07
There's two windows vista entries because they point to different partitions. Do you have two separate windows vista installations? :confused:

---

### Post by falcon61102 on 2008-12-07
Could be two different installs or it could be a number of other options like system restore tools or a media direct partition.  All of which are handled by the GRUB pretty much in the same manner as an actual windows install.

---

### Post by ItsManaged on 2008-12-07
You may want to have a look at [start up manager]("http://web.telia.com/~u88005282/sum/index.html")

Start up manager gives you a GUI to grub and manages some tasks for you.

If you like it, you can install it via Add/Remove.

---

### Post by sellwowgold2 on 2008-12-07
[size=2][color=#282827][color=#000000][sell wow gold](http://www.virdeal.com),[sell ffxi gil](http://www.virdeal.com),[sell maple story mesos](http://www.virdeal.com),[sell gaia gold](http://www.virdeal.com) [http://www.virdeal.com](http://www.virdeal.com) [/color][/color][/size]

---

