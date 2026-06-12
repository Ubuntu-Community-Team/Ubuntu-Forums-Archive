---
title: "Cannot run Add/Remove or update manager"
date: 2009-04-01
forum: General Help
---

### Post by bluTaz on 2009-04-01
Hey guys, I've switched over to Ubuntu from Vista almost a year ago and its been a Journey, lol, but I prefer Ubuntu over Windows at most. Now I'm stuck on a problem here, while trying to fix the mic problem on my Dell Inspiron 1525, after installing a package from the dell website, linux-backports-modules-2.6.22-14-generic_2.6.22-14.50_i386.deb .... I was unable to run Add/Remove and Update Manager, following some other instructions off of older problems, I am unable to fix it.

tried: 

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

results:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-backports-modules-2.6.22-14-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 6119kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 141348 files and directories currently installed.)
Removing linux-backports-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-backports-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


any ideas on how to fix this? Thanks in advance guys

---

### Post by dcstar on 2009-04-01
> **bluTaz said:**
> Hey guys, I've switched over to Ubuntu from Vista almost a year ago and its been a Journey, lol, but I prefer Ubuntu over Windows at most. Now I'm stuck on a problem here, while trying to fix the mic problem on my Dell Inspiron 1525, after installing a package from the dell website, **linux-backports-modules**-2.6.22-14-generic_2.6.22-14.50_i386.deb .... I was unable to run Add/Remove and Update Manager, following some other instructions off of older problems, I am unable to fix it.
.........
any ideas on how to fix this? Thanks in advance guys

Go into Synaptic and reinstall that package.

---

### Post by bluTaz on 2009-04-01
Thanks for help, tried complete removal since reinstall option wasn't available and result:



E: linux-backports-modules-2.6.22-14-generic: subprocess post-removal script returned error exit status 1

---

### Post by bluTaz on 2009-04-01
any other ideas would be appreciated guys... thnks

---

### Post by bluTaz on 2009-04-01
This is the message I get when trying to run Add/Remove:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

