---
title: "Splashy won't install in jaunty?"
date: 2009-05-09
forum: General Help
---

### Post by ashour on 2009-05-09
hi
i was trying to get my ubuntu to look like make following this tutorial

but in the part where i should change the splashy screen i remove usplash but whenever i try to install splashy it fails giving this error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  usplash usplash-theme-ubuntu
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 774kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 108639 files and directories currently installed.)
Removing usplash-theme-ubuntu ...
update-initramfs: deferring update (trigger activated)
Removing usplash ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
Processing triggers for man-db ...
ashour@Ashour:~$ sudo su -
root@Ashour:~# sudo apt-get install splashy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  splashy-themes console-common
The following NEW packages will be installed:
  splashy
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1180kB of archives.
After this operation, 1831kB of additional disk space will be used.
(Reading database ... 108622 files and directories currently installed.)
Unpacking splashy (from .../splashy_0.3.13-3ubuntu1_i386.deb) ...
mv: cannot stat `/etc/splashy/themes': No such file or directory
dpkg: error processing /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

i tryied dpkg --force-install for the package debian file but didn't work too 

also when i tried to reinstall usplash it boots up and closes with the splashy screen missplaced

---

