---
title: "can't update 11.04"
date: 2011-05-14
forum: Desktop Environments
---

### Post by ve3tru on 2011-05-14
I cant install anything, and I cant update it either
Please help

peter@peter-laptop:~$ sudo apt-get install -f
[sudo] password for peter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-2.6.32-24-generic linux-image-2.6.35-19-generic
  linux-image-2.6.35-20-generic linux-image-2.6.35-21-generic
0 upgraded, 0 newly installed, 4 to remove and 1602 not upgraded.
12 not fully installed or removed.
After this operation, 544MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 200357 files and directories currently installed.)
Removing linux-image-2.6.32-24-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
/etc/default/grub: 9: quiet: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-24-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.35-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-19-generic /boot/vmlinuz-2.6.35-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-19-generic /boot/vmlinuz-2.6.35-19-generic
/etc/default/grub: 9: quiet: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-19-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.35-20-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-20-generic /boot/vmlinuz-2.6.35-20-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-20-generic /boot/vmlinuz-2.6.35-20-generic
/etc/default/grub: 9: quiet: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-20-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-20-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.35-21-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-21-generic /boot/vmlinuz-2.6.35-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-21-generic /boot/vmlinuz-2.6.35-21-generic
/etc/default/grub: 9: quiet: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-21-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-21-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.32-24-generic
 linux-image-2.6.35-19-generic
 linux-image-2.6.35-20-generic
 linux-image-2.6.35-21-generic
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
peter@peter-laptop:~$

---

### Post by Frogs Hair on 2011-05-14
Are you upgrading ? The reason I ask is because some of the kernels listed appear to be from Maverick and Lucid .

---

### Post by THE CARTER on 2011-05-14
You may just want to use a live cd to upgrade. That is always a lot easier and rarely has problems (and takes 20 minutes instead of 20 hours).

Download it from ubuntu's homepage and follow their instructions.

---

### Post by ve3tru on 2011-05-15
I have already upgraded to 11.04 but it says in my system monitor 10.10 maveric
but cant upgrade install delete anything at this point.
Maybe its time for a clean install, but thats a pain got lots of stuff here

---

