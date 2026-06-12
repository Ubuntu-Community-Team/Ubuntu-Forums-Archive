---
title: "linux-image-386 removed while installing Wine"
date: 2005-12-26
forum: Desktop Environments
---

### Post by quazar on 2005-12-26
During the installation of Wine, linux-image-386 was removed. I hoped to reinstall it after installing Wine. However Synaptic installation failed as did apt-get install linux-image-386
I'm afraid this module is quite essential to Ubuntu. Currently it appears to be running fine (though I think iU means Uninstalled?):

~\dpkg -l | grep 386
ii  linux-headers-2.6.12-9-386            2.6.12-9.23                          L inux kernel headers 2.6.12 on 386
ii  linux-image-2.6.12-9-386              2.6.12-9.23                          L inux kernel image for version 2.6.12 on 386
iU  linux-image-386                       2.6.12.16.1                          L inux kernel image on 386.
ii  linux-restricted-modules-2.6.12-9-386 2.6.12.4-11                          N on-free Linux 2.6.12 modules on 386
ii  mplayer-386                           1.0-pre7cvs20050716-0.1ubuntu9       T he Ultimate Movie Player For Linux

Can I safely reboot my PC?
How can I re-install linux-image-386?

**I'm using Ubuntu for a month or two now, and I think this is my first major screw-up :) **

---

### Post by kaamos on 2005-12-26
[QUOTE=quazar]
ii  linux-image-2.6.12-9-386              2.6.12-9.23                          L inux kernel image for version 2.6.12 on 386[/QUOTE]
This is a kernel image, so it should be safe to reboot.. What is the output of this
```
sudo apt-get install linux-image-2.6.12-10-386
```

---

### Post by quazar on 2005-12-26
Preconfiguring packages ...
(Reading database ... 144162 files and directories currently installed.)
Unpacking linux-image-2.6.12-10-386 (from .../linux-image-2.6.12-10-386_2.6.12-10.25_i386.deb) ...
The directory /lib/modules/2.6.12-10-386 still exists. Continuing as directed.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.12-10-386_2.6.12-10.25_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive: Success
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.14-ck1
Found kernel: /boot/vmlinuz-2.6.12-10-386
Found kernel: /boot/vmlinuz-2.6.12-9-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.12-10-386_2.6.12-10.25_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dcstar on 2005-12-26
[QUOTE=quazar]During the installation of Wine, linux-image-386 was removed. I hoped to reinstall it after installing Wine. However Synaptic installation failed as did apt-get install linux-image-386
I'm afraid this module is quite essential to Ubuntu. Currently it appears to be running fine (though I think iU means Uninstalled?):
......
Can I safely reboot my PC?
How can I re-install linux-image-386?

**I'm using Ubuntu for a month or two now, and I think this is my first major screw-up :) **[/QUOTE]
Firstly, that package seems only to contain a couple of text files, so it isn't really important.

Secondly, unless you are using an ancient 386 or 486 processor, you really should be using a "686" kernel (or a K7 one if you use an AMD processor), look at this:

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

