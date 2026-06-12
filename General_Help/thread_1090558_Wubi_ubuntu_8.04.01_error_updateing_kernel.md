---
title: "Wubi ubuntu 8.04.01 error updateing kernel"
date: 2009-03-08
forum: General Help
---

### Post by klein de usa on 2009-03-08
hi 
we did an install using Wubi install of 8.04.01 now when we try updating the system we get this error 

Unpacking replacement linux-image-2.6.24-19-generic ...

 dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb (--unpack):
 
 unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version: Operation not permitted
 
dpkg-deb: subprocess paste killed by signal (Broken pipe)
 
Running postrm hook script /sbin/update-grub.
 
Searching for GRUB installation directory ... found: /boot/grub
 
Searching for default file ... found: /boot/grub/default
 
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
 Searching for splash image ... none found, skipping ...
 
Found kernel: /boot/vmlinuz-2.6.24-23-generic
 
Found kernel: /boot/vmlinuz-2.6.24-19-generic
 
Found kernel: /boot/memtest86+.bin
 Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 
 /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb
  
/var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb
 
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
A package failed to install.  Trying to recover:

apt-get -f   <tried this got the same thing 

any ideas ??????????????????

---

