---
title: "error: no such file (in LFS project)"
date: 2012-10-30
forum: Development CD/DVD Image Testing
---

### Post by erkaninho on 2012-10-30
I wanted to create a minimal LFS project, which consists of bash, grub, and kernel. I have bash 4.2 and kernel 3.5.2. I compiled, made them, and have image file of the kernel and executable of bash. I have them in /mnt/lfs folder. There I have three folder boot, bin and lib, inside lib, I have the libraries that are needed for bash, inside bin I have the bash folder and the sh executable, and inside boot, I have my kernel image and config file. I used my 1GB, /dev/sda6 partition for mounting it to /mnt/lfs. When I start my PC I have it under Grub menus, but when I try to start it, it gives me error saying no file found. I have those commands in the grub config:

menuentry 'GNU/Linux, Linux 3.5.2-lfs-7.2' {
    set default=0
    set timeout=5

    insmod part_msdos
    insmod ntfs
    insmod ext2

    set root='(hd0,msdos6)'
    echo 'Loading LFS...'

    linux    /boot/vmlinuz-3.5.2-lfs-7.2 root=/dev/sda6 rootdelay=7
}

To make it clear, my kernel name is: vmlinuz-3.5.2-lfs-7.2, and I have mounted them in /dev/sda6

Any opinion?

---

