---
title: "Linux Dual Boot Woes"
date: 2009-06-13
forum: General Help
---

### Post by Nexusx6 on 2009-06-13
Hola,

I've been using Ubuntu for a few years now, and I decided that I'd like to try out other distro, but the fact that I'm on a fakeRAID 0 has reared is ugly head at me once again :(

My HD is separated into  3 primary partitions: root, swap, /home. Because I already have 3 primary I can only add one more, this being the case I got gparted and made the last partition an extended one so I could keep adding more distro's -- and here is where things went a little awry.

First, fdisk and cfdisk no longer work at all :(. My drives don't map like sda1, sda2 etc either. I got Arch installed, but I cant' access it because Grub gives me an Error:15, can't find file, and I can't mount the Arch partition to find the name of the kernel file I should be pointing to because fdisk is borked.

Here's some info from the terminal

```
sudo fdisk -l

Unable to seek on /dev/sda

```
```
sudo cfdisk

FATAL ERROR: Bad primary partition 2: Partition ends after end-of-disk   
Press any key to exit cfdisk

```
```
/dev/mapper/
total 0
drwxr-xr-x  2 root root     160 2009-06-13 11:46 .
drwxr-xr-x 16 root root    4020 2009-06-13 11:52 ..
crw-rw----  1 root root  10, 61 2009-06-13 11:46 control
brw-rw----  1 root disk 252,  0 2009-06-13 11:46 nvidia_ghhhfege
brw-rw----  1 root disk 252,  1 2009-06-13 11:46 nvidia_ghhhfege1
brw-rw----  1 root disk 252,  2 2009-06-13 11:46 nvidia_ghhhfege2
brw-rw----  1 root disk 252,  3 2009-06-13 11:51 nvidia_ghhhfege3
brw-rw----  1 root disk 252,  4 2009-06-13 11:46 nvidia_ghhhfege5

```

This is what the tail end of Grub looks like:
```
title           Arch Linux
root            (hd0,4)
kernel          /boot/vmlinuz26 root=/dev/mapper/nvidia_ghhhfege5 ro vga=773
initrd          /boot/kernel26.img

```

I know it's kind of a long post, but I would really appreciate any help. I can boot into Ubuntu and all my files are just fine, but I would really like to be able to tinker with other distro's as well. Any help is reall appreciated.

---

