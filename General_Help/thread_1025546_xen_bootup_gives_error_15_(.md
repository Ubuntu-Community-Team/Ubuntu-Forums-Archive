---
title: "xen bootup gives error 15 :("
date: 2008-12-30
forum: General Help
---

### Post by Surabhi123 on 2008-12-30
Hi,
I am using Ubuntu 8.04..over which i have installed Virtual Box. The single Virtual machine on Virtual Box also runs Ubuntu 8.04. I am trying to install xen 3.2.2 from source on this virtual machine. the compilation succeeds and is installing everything in the boot directory as it should. 
I have added the following entry in the menu.lst.


title           Xen 3.0 / XenLinux 2.6
root            (hd0,0)
kernel          /boot/xen-3.2.2.gz dom0_mem=262144
module          /boot/vmlinuz-2.6.18.8-xen root=/dev/sda1 ro console=tty0
module          /boot/initrd-2.6.18.8-xen.img


However, I am getting an Error 15 while trying to boot xen.
The ubuntu is intact and boots up fine...

Any clue as to what is happening??

Thanks a lot in anticipation...

Surabhi

---

