---
title: "Failed initramfs update"
date: 2009-04-29
forum: General Help
---

### Post by Machinista on 2009-04-29
Hi,

I'm running Jaunty 9.04 AMD64 flavour.

Some updates arrived this morning, but were not cleanly installed.  I got the following errors:

> <name>@<name>-desktop:/$ sudo dpkg --configure -a Setting up initramfs-tools (0.92bubuntu29) ...

update-initramfs: deferring update (trigger activated)



dpkg: dependency problems prevent configuration of cnijfilter-ip1800series:

 cnijfilter-ip1800series depends on libglib1.2 (>= 1.2.0); however:

  Package libglib1.2 is not installed.

 cnijfilter-ip1800series depends on libgtk1.2 (>= 1.2.10-4); however:

  Package libgtk1.2 is not installed.

 cnijfilter-ip1800series depends on libxml1 (>= 1:1.8.14-3); however:

  Package libxml1 is not installed.

dpkg: error processing cnijfilter-ip1800series (--configure):

 dependency problems - leaving unconfigured Processing triggers for initramfs-tools ...

update-initramfs: Generating /boot/initrd.img-2.6.28.9-custom Cannot find /lib/modules/2.6.28.9-custom

update-initramfs: failed for /boot/initrd.img-2.6.28.9-custom

dpkg: subprocess post-installation script returned error exit status 1 <name>@<name>-desktop:/$


I have been experimenting with kernel conifgs, but have reverted to 2.6.28-11-generic; however, despite using Janitor to clean out the custom kernel, there's still some lingering presense.

How can I clean this up?

TIA.

---

### Post by Machinista on 2009-05-16
Fixed by installing/reinstalling NVIDEA-COMMON

---

