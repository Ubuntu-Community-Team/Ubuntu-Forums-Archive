---
title: "apt-get upgrade Error."
date: 2006-08-06
forum: Desktop Environments
---

### Post by ntnwwnet on 2006-08-06
I tried updating my Dapper Drake installer (it's used as a server), and got all these errors. Being a complete Linux n00b, I have no idea what they mean.

Thanks for your help.

```

nil@guardian:/ # sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  gdk-imlib1 php4-interbase
The following packages will be upgraded:
  linux-image-2.6.15-26-386
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
82 not fully installed or removed.
Need to get 0B/21.7MB of archives.
After unpacking 81.9kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 97969 files and directories currently installed.)
Preparing to replace linux-image-2.6.15-26-386 2.6.15-26.45 (using .../linux-image-2.6.15-26-386_2.6.15-26.46_i386.deb) ...
The directory /lib/modules/2.6.15-26-386 still exists. Continuing as directed.
Unpacking replacement linux-image-2.6.15-26-386 ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.15-26-386_2.6.15-26.46_i386.deb (--unpack):
 failed in buffer_write(fd) (9, ret=-1): backend dpkg-deb during `./boot/vmlinuz-2.6.15-26-386': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.15-26-386
Found kernel: /vmlinuz-2.6.15-23-386
Found kernel: /vmlinuz-2.6.12-10-386
Found kernel: /vmlinuz-2.6.12-9-386
Found kernel: /vmlinuz-2.6.10-5-386
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.15-26-386_2.6.15-26.46_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
nil@guardian:/ #

```

I have a status page of the machine up on the internet if it would help, [http://www.nwwnetwork.net/status]("http://www.nwwnetwork.net/status")

---

