---
title: "Resize Var remotely via SSH"
date: 2009-02-03
forum: General Help
---

### Post by Gorlist on 2009-02-03
Hi, ive got a webserver which I just reimaged from FC4 to Ubuntu 8.04 LTS, and to my horror found my var directory is far too small to be used with the plesk control panel. 

Unfortunately I only have remote SSH access, and no control over the imaging. 

Raid 1, software.

What I would like todo is effectively swap home for var (or atleast their partition size). Ive read up on using "parted" however don't fully understand how the start, and end corresponds to fdisk -l and df -h outputs.


> Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              950M  390M  512M  44% /
varrun                485M   84K  485M   1% /var/run
varlock               485M     0  485M   0% /var/lock
udev                  485M   76K  485M   1% /dev
devshm                485M     0  485M   0% /dev/shm
/dev/md5              4.7G  554M  4.2G  12% /usr
/dev/md6              4.7G  376M  4.3G   8% /var
/dev/md7               63G  4.6M   63G   1% /home
none                  485M  376K  485M   1% /tmp

so would I:

parted resize 7 70290 76290    (which would move the start of home and make it only 6gig in total)
parted resize 6 7590 70290     (then make var take up the free space)

Any suggestions?

---

### Post by dcstar on 2009-02-03
> **Gorlist said:**
> Hi, ive got a webserver which I just reimaged from FC4 to Ubuntu 8.04 LTS, and to my horror found my var directory is far too small to be used with the plesk control panel. 

Unfortunately I only have remote SSH access, and no control over the imaging. 

Raid 1, software.

What I would like todo is effectively swap home for var (or atleast their partition size). Ive read up on using "parted" however don't fully understand how the start, and end corresponds to fdisk -l and df -h outputs.


Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              950M  390M  **512M  44% /**
varrun                485M   84K  485M   1% /var/run
varlock               485M     0  485M   0% /var/lock
udev                  485M   76K  485M   1% /dev
devshm                485M     0  485M   0% /dev/shm
/dev/md5              4.7G  554M  4.2G  12% /usr
/dev/md6              4.7G  376M  **4.3G**   8%** /var**
/dev/md7               63G  4.6M   63G   1% /home
none                  485M  376K  485M   1% /tmp

Any suggestions?

You are joking, aren't you? You have 4.3G free in your /var right now, what makes you think you need more?

The root filesystem is a problem, there is only 512MB available there and it is a ridiculously small partition.

Anyway, you cannot resize mounted partitions, all of this has to be done on umounted partitions.

---

### Post by Gorlist on 2009-02-03
> **dcstar said:**
> You are joking, aren't you? You have 4.3G free in your /var right now, what makes you think you need more?

The root filesystem is a problem, there is only 512MB available there and it is a ridiculously small partition.

Anyway, you cannot resize mounted partitions, all of this has to be done on umounted partitions.

Im afraid not. Plesk stores all of its files from within var, so sites, databases etc.

I need it something more like this:

> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/md1              950M  137M  765M  16% /
/dev/md5              4.7G  2.1G  2.6G  46% /usr
/dev/md7               63G  110M   63G   1% /var
/dev/md6              4.7G  4.4M  4.7G   1% /home
none                  485M     0  485M   0% /tmp


Its probably not possible without major headache.

---

### Post by dcstar on 2009-02-03
> **Gorlist said:**
> Im afraid not. Plesk stores all of its files from within var, so sites, databases etc.

I need it something more like this:

Please don't quote stuff in posts, use the CODE function.

Simply make a link into the free space in the /home partition for any large directories under /var and you problem will be solved without repartitioning.

---

### Post by Gorlist on 2009-02-03
Someone had suggest a symlink? but im not sure how this would effect plesk itself. Sorry in regards to quotes, its been long night, couldn't see the code button :)

---

