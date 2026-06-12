---
title: "problems with update dependencies"
date: 2008-12-28
forum: General Help
---

### Post by nloewen on 2008-12-28
I just did a clean install of ubuntu 8.10 on my acer travelmate 2300. I was useing a netgear card and after converting and installing the windows driver I did updates. I can no longer use dpkg, apt-get, or symantic. It gave me these errors and I can't seem to fix them.

E: samba-common: subprocess post-installation script returned error exit status 1
E: smbclient: dependency problems - leaving unconfigured
E: udev: subprocess post-installation script returned error exit status 1
E: linux-image-2.6.27-7-generic: subprocess post-installation script returned error exit status 2
E: linux-image-2.6.27-9-generic: subprocess post-installation script returned error exit status 2
E: linux-restricted-modules-2.6.27-9-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

It told me to run "dpkg --configure -a" and it gave this output.

Setting up samba-common (2:3.2.3-1ubuntu3.3) ...
readlink: No such file or directory
ucf: Unable to determine The new file
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.2.3-1ubuntu3.3); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
Setting up initramfs-tools (0.92bubuntu16) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.27-7-generic (2.6.27-7.16) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
readlink: No such file or directory
/usr/sbin/mkinitramfs: 299: cannot create : Directory nonexistent
cpio: not implemented or invalid option --
update-initramfs: failed for /boot/initrd.img-2.6.27-7-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.27-7-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up udev (124-9) ...
ln: invalid option -n
dpkg: error processing udev (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-image-2.6.27-9-generic (2.6.27-9.19) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-9-generic
readlink: No such file or directory
cpio: not implemented or invalid option --
/usr/sbin/mkinitramfs: 299: cannot create : Directory nonexistent
update-initramfs: failed for /boot/initrd.img-2.6.27-9-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.27-9-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.27-9-generic:
 linux-restricted-modules-2.6.27-9-generic depends on linux-image-2.6.27-9-generic; however:
  Package linux-image-2.6.27-9-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.27-9-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.27-9-generic; however:
  Package linux-image-2.6.27-9-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.27-9-generic; however:
  Package linux-restricted-modules-2.6.27-9-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.27.9.13); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.27.9.13); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
readlink: No such file or directory
cpio: not implemented or invalid option --
/usr/sbin/mkinitramfs: 299: cannot create : Directory nonexistent
update-initramfs: failed for /boot/initrd.img-2.6.27-7-generic
dpkg: subprocess post-installation script returned error exit status 1

I'm not sure what to do. There seems to be a problem with dependencies. Possibly readlink. If I could get some help that would be great.

---

### Post by manishr on 2009-01-08
I am getting a similar problem with the same kernel without the samba error. Its a new build. I tried disabling the restricted driver (video card) and doing a sudo apt-get update then upgrade. I do not understand why initramfs is failing. If anyone can help, it would be appreciated.

here's my error:

Setting up linux-restricted-modules-2.6.27-9-generic (2.6.27-9.13) ...
update-initramfs: Generating /boot/initrd.img-2.6.27-9-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.27-9-generic
dpkg: error processing linux-restricted-modules-2.6.27-9-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.27-9-generic; however:
  Package linux-restricted-modules-2.6.27-9-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-restricted-modules-generic (= 2.6.27.9.13); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                       Errors were encountered while processing:
 linux-restricted-modules-2.6.27-9-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

