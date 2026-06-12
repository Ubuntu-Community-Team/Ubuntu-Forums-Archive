---
title: "Grub Error 15 - File not found"
date: 2009-06-19
forum: General Help
---

### Post by IGITIHI on 2009-06-19
I recently deleted some old kernel files (linux-image) using synaptic. Then I shut the pc down and when I tried to boot again, I recieved grub error 15: File not found.

I guess I deleted the wrong kernel files because I have a dual boot system and I can still boot into XP but not in Ubuntu. How can I fix this? Any help will be appreciated. Thank you in advance!

---

### Post by cyclobs on 2009-06-19
it's most likely trying to boot from a kernal that isn't there. which kinda sucks and affink the only thing you can do is reinstall the system

---

### Post by Gunman1982 on 2009-06-19
If you want to keep your system you can go a road which is slightly more interesting than reinstalling ubuntu.

Boot your live cd, mount your partition on which you have ubuntu installed, copy the kernel of your live cd into the /boot/ directory of your ubuntu installation, change the /boot/grub/menu.lst so that the entry matches the copied kernelname, save, unmount. Reboot without livecd.

For a more detailed walkthrough either google a bit or ask again ;-) .

A little tip: rather than copying the kernel from the live cd (which is probably an old one), load the actual one from the web and save it into the /boot/ directory of your ubuntu installation.

---

### Post by IGITIHI on 2009-06-19
The first entry in grub is "ubuntu 8.04.1, kernel 2.6.24-19-generic". So, which kernel should I download? Can I download it from the Linux Kernel Archives? And what shoul I do with the downloaded files? Just decompress them and copy them to /boot/ ?

[edit]: after hours of searching in the forum, I did the following things:

1)Booted using a live CD
2)Mounted my linux partition using places->removable media. mount point was /media/disk
3)opened a terminal and typed the following:

```
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount --bind /dev/ /media/disk/dev
root@ubuntu:~# mount --bind /dev/pts /media/disk/dev/pts
root@ubuntu:~# mount --bind /dev/shm /media/disk/dev/shm
root@ubuntu:~# cp -L /etc/resolv.conf /media/disk/etc/
root@ubuntu:~# chroot /media/disk
root@ubuntu:/# mount -t sysfs sysfs /sys
root@ubuntu:/# mount -t proc proc /proc
```

So far, everything seemed to work. But then I typed

```
apt-get purge linux-image-2.6.24.19-generic
```

and I got the following output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-image-2.6.24.19-generic
root@ubuntu:/# apt-get install linux-image-2.6.24-19-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-2.6.24-19-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.24-19-generic (2.6.24-19.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So, what am I doing wrong here?

[edit2]
I finally solved this, thanks to HymnToLife from the ubuntuforums irc channel. I turned out that I had a separate boot partition (/dev/sdb3/) and so i had to do the following:

1) I booted using a live cd and mounted my root partition at /media/disk. Then:
```
sudo mount /dev/sdb2 /media/disk/boot
$ sudo -i
# mount --bind /dev/ /media/disk/dev

# mount --bind /dev/pts /media/disk/dev/pts

# mount --bind /dev/shm /media/disk/dev/shm

# cp -L /etc/resolv.conf /media/disk/etc/

# chroot /media/disk

# mount -t sysfs sysfs /sys

# mount -t proc proc /proc 

# apt-get purge linux-image-2.6.24-19-generic

# apt-get install linux-image-2.6.24-19-generic

# exit

# exit

$ exit
```

---

