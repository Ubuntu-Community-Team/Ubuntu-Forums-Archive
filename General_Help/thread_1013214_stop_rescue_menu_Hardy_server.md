---
title: "stop rescue menu Hardy server"
date: 2008-12-16
forum: General Help
---

### Post by seanbarman on 2008-12-16
Hi,

I have installed hardy server kernel with pae so i can use 6gb of ram,
but it always boots up to rescue menu asking

drop to shell
xfix fix xerver
continue to boot

I would like to disable this as xserver is working fine with nvidia driver

thanks.

title		Ubuntu 8.04, kernel 2.6.24-22-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-server root=UUID=09097db1-cbac-474a-9907-3369f0f60aa3 ro splash vga=normal  
initrd		/boot/initrd.img-2.6.24-22-server
quiet

---

