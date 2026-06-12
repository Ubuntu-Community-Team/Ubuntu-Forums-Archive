---
title: "ubuntu &amp; centos"
date: 2008-06-24
forum: Desktop Environments
---

### Post by devgon on 2008-06-24
hello all,

i install windows xp in 10 GB. then install centos4.4 in other partition. there is one / partition in centos.

now i want install ubuntu7.10 without delete my previous OS.

my HDD is 40GB. i want install ubuntu7.10 in extra 10GB.

plz, say me how i can do this.
is it possible.

---

### Post by mali2297 on 2008-06-24
Yes, of course. The procedure is basically the same as when you set up a dual boot. You can make room for Ubuntu beforehand or during the installation. Ubuntu and CentOS can share the same swap partition (although you might need to edit fstab in CentOS afterwards).

See this [link]("https://help.ubuntu.com/community/WindowsDualBoot").
> 
Manual partitioning
   1. Choose "Manually edit partition table"
          * Listed will be your current partitions
   2. Select the partition you want to resize and press Enter.
   3. Select "Size:", press Enter.
   4. Select Yes, press Enter.
   5. Type in a new size in Gigabytes for your partition, it's recommended you free up AT LEAST 10 GB of free space for your Ubuntu install. Press Enter when happy with your changes. It may take some time to apply the changes.
   6. Create a swap partition of at least your amount of RAM (if you don't know, 2000 MB is a good value).
   7. Create a partition for your Ubuntu installation, at least 10 GB.
   8. Select "Finish partitioning and write changes to disk".


Ubuntu will install the boot loader GRUB which should be able to recognize both Windows and CentOS.

---

