---
title: "Basic System installed."
date: 2007-10-10
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2007-10-10
Hi All,

I have a windows system and have a 15GB HDD and a 4GB HDD seperatly.

On 15GB I have 2 partitions and on one partition of 11.5GB I have windows in it.

I installed Ubuntu on 4GB HDD and is working fine. Unfortunetly I have a basic installetion in it.

I wanted to use Ubuntu to install LAMP (Apache, MySQL and PHP). Please help me installing those softwares because I cannot do it through synaptic pkage manager.

Very important thing I wanted to say is, In Windows HDD I wanted to use second partition to linux that is 2.5GB which is now empty.

Please suggest me how to do it.

Thanks in advance.

Regards,

Swaroop Kunduru.

---

### Post by gibbsnich on 2007-10-12
Please see [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) for instructions on how to install LAMP (BTW: google is your friend :)).
Then use a tool like gparted to prepare the partition you want to use in Ubuntu. You'd then have to edit /etc/fstab to permanently mount the partition in Ubuntu - remember that /etc/fstab is an important file, so before modifying it better make a backup..

HTH!
Michael

---

