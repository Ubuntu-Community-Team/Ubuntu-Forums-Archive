---
title: "Error while install/uninstall apps from software center"
date: 2013-06-16
forum: Desktop Environments
---

### Post by todorakiggg on 2013-06-16
After the recent updates I've installed I got the following error when installing or uninstalling apps from Ubuntu Software center on Ubuntu 13.04:

installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 332535 files and directories currently installed.)
Removing gelemental ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for menu ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Setting up linux-image-extra-3.8.0-25-generic (3.8.0-25.37) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-25-generic /boot/vmlinuz-3.8.0-25-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-25-generic /boot/vmlinuz-3.8.0-25-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-25-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.8.0-25-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-extra-3.8.0-25-generic.postinst line 1010.
dpkg: error processing linux-image-extra-3.8.0-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.8.0-25-generic; however:
  Package linux-image-extra-3.8.0-25-generic is not configured yet.


dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.8.0.25.43); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 linux-image-extra-3.8.0-25-generic
 linux-image-generic
 linux-generic
Error in function: 
Setting up linux-image-extra-3.8.0-25-generic (3.8.0-25.37) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-25-generic /boot/vmlinuz-3.8.0-25-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-25-generic /boot/vmlinuz-3.8.0-25-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-25-generic


gzip: stdout: No space left on device
cpio: write error: Broken pipe
E: mkinitramfs failure cpio 1 gzip 1
update-initramfs: failed for /boot/initrd.img-3.8.0-25-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-extra-3.8.0-25-generic.postinst line 1010.
dpkg: error processing linux-image-extra-3.8.0-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.8.0-25-generic; however:
  Package linux-image-extra-3.8.0-25-generic is not configured yet.


dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured


It says there is not space left on the device, but I actually have plenty of space, the only partition that has 24 MB free is the boot partition, but how to access is it and what to do there if this is the problem?

---

### Post by todorakiggg on 2013-06-16
Issue solved with removing the old kernels: [http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/)

---

### Post by ajgreeny on 2013-06-16
Is there a good reason for your having a separate /boot partition?

This is precisely the sort of problem that a separate /boot can make, and why it is generally better not to run a system with one, though I accept there are situations where it is needed.

---

### Post by ShadowVegan on 2013-06-16
I'm not sure on all of your issues but the dependency issues should be able to be fixed with
```
sudo apt-get -f install
```

It also looks like one of your devices it out of space so perhaps you could upgrade the device to something bigger.

---

### Post by todorakiggg on 2013-06-17
Thanks for your involvement.
Is there a reason for separate boot partition? Well, I am not sure, when I made clean 13.04 install, it made the partitions itself :). I was surprised to see that as well. Besides the partition is 258 MB only.
Otherwise Ubuntu is installed on 128 GB SSD drive and 70% is available on it...
I have regular HDD for the rest of crap I store :D

Do you have an idea how to make the boot partition bigger? I did not see gparted to offer such an option...

---

### Post by ajgreeny on 2013-06-19
Is your boot partition an EFI partition, needed if you install on a computer with UEFI instead of old style BIOS?

If that is the case, that partition is not really a separate /boot partition, merely a small partition which contains small boot files for each OS on your machine, and which is mounted at /boot/efi, and I suspect has little to do with your original problem.

---

