---
title: "File size-related HELP!"
date: 2009-06-22
forum: General Help
---

### Post by Waisybabu on 2009-06-22
I recently installed Ubuntu Jaunty Jackalope 9.04 on my laptop (Pentium M 1.6GHz, DDR2 512MB RAM and 64MB ATi Mobility Radeon 9200) and I ***_love_*** it!

I'll give my reasons later because at the moment I need your help.

**_Problem_**
I installed Ubuntu by making a new partition SPECIFICALLY for it. I named it the U: drive since the partitioner gave me the option. I also *chose "3GB"* when the installer asked me how much should the file size of the OS should be.

Now. U: Drive has 5Gigs in it. (Windows tells me that..) Ubuntu uses only 3.6GB and there is **1.74*GB*** of space left. All fine and good, eh?

*Now* when I use Ubuntu, it tells me that root drive/file system has only **7.8*MB*** in it. WHAT THE HECK?

I can't install new apps nor can I open really heavy programs like OpenOffice. What do I do, what do I do!?

Will I have to reinstall with a 4GB OS Files size? Or is there a workaround to it because either way, this is VERY stupid.

---

### Post by hal8000 on 2009-06-22
> **Waisybabu said:**
> I recently installed Ubuntu Jaunty Jackalope 9.04 on my laptop (Pentium M 1.6GHz, DDR2 512MB RAM and 64MB ATi Mobility Radeon 9200) and I ***_love_*** it!

I'll give my reasons later because at the moment I need your help.

**_Problem_**
I installed Ubuntu by making a new partition SPECIFICALLY for it. I named it the U: drive since the partitioner gave me the option. I also *chose "3GB"* when the installer asked me how much should the file size of the OS should be.

Now. U: Drive has 5Gigs in it. (Windows tells me that..) Ubuntu uses only 3.6GB and there is **1.74*GB*** of space left. All fine and good, eh?

*Now* when I use Ubuntu, it tells me that root drive/file system has only **7.8*MB*** in it. WHAT THE HECK?

I can't install new apps nor can I open really heavy programs like OpenOffice. What do I do, what do I do!?

Will I have to reinstall with a 4GB OS Files size? Or is there a workaround to it because either way, this is VERY stupid.


You have installed using wubi which is not the same as installing linux on its own partition.
Can you post the output from a terminal of:
df

This will show how the system has been partitioned

---

### Post by donato roque on 2009-06-22
The minimum hd space for the installation is 4GB for a regular
install.  The recommended size is 8GB.  I use 4.7GB for the
\ partition myself.

---

### Post by Waisybabu on 2009-06-22
> **hal8000 said:**
> You have installed using wubi which is not the same as installing linux on its own partition.
Can you post the output from a terminal of:
df

This will show how the system has been partitioned

Here is the report:

Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                       2765720   2619612      5616 100% /
tmpfs                   254400         0    254400   0% /lib/init/rw
varrun                  254400       112    254288   1% /var/run
varlock                 254400         0    254400   0% /var/lock
udev                    254400       156    254244   1% /dev
tmpfs                   254400       548    253852   1% /dev/shm
/dev/sda6              5662880   3835472   1827408  68% /host
lrm                     254400      2392    252008   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda5             38290892  31104716   7186176  82% /media/Media
/dev/sda1             14651248  13970172    681076  96% /media/System Software

---

### Post by Waisybabu on 2009-06-22
> **donato roque said:**
> The minimum hd space for the installation is 4GB for a regular
install.  The recommended size is 8GB.  I use 4.7GB for the
\ partition myself.

I did the 3GB install :confused:

---

### Post by nothingspecial on 2009-06-22
> **Waisybabu said:**
> Here is the report:

Filesystem           1K-blocks      Used Available Use% Mounted on
/host/ubuntu/disks/root.disk
                       [COLOR="Red"]2765720   2619612      5616 100% /[/COLOR]
tmpfs                   254400         0    254400   0% /lib/init/rw
varrun                  254400       112    254288   1% /var/run
varlock                 254400         0    254400   0% /var/lock
udev                    254400       156    254244   1% /dev
tmpfs                   254400       548    253852   1% /dev/shm
/dev/sda6              5662880   3835472   1827408  68% /host
lrm                     254400      2392    252008   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda5             38290892  31104716   7186176  82% /media/Media
/dev/sda1             14651248  13970172    681076  96% /media/System Software

Yep your full. You should really use 5gig + for a ubuntu install. I use 10 for root. If you have nothing of value saved a reinstall to a larger partition would be easiest.

Plus if everything works and you like ubuntu, I suggest you do a full instalation rather than wubi.

Also, if you use the -h flag with df it will provide human readable output, ie your patition information in gigabytes. df -h

---

### Post by Waisybabu on 2009-06-22
> **nothingspecial said:**
> Yep your full. You should really use 5gig + for a ubuntu install. I use 10 for root. If you have nothing of value saved a reinstall to a larger partition would be easiest.

Plus if everything works and you like ubuntu, I suggest you do a full instalation rather than wubi.

Also, if you use the -h flag with df it will provide human readable output, ie your patition information in gigabytes. df -h

GAhhh! Install it [I]again?!
[/I]
Isn't there ANY work around to it? Windows still tells me there is 1.7GB free on the U: drive :(

---

### Post by unutbu on 2009-06-22
Here are instructions on resizing the Wubi filesystem. (Search for resizeroot): [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

The only snag is, you'll need room to install the lvpm package...

Maybe if you can purge some non-essential packages, you could make room?

Maybe open a terminal (Applications>Accessories>Terminal) and type
```

sudo apt-get clean all
```
This will clean out /var/cache/apt/archives and /var/cache/apt/archives/partial.

---

### Post by Waisybabu on 2009-06-22
> **unutbu said:**
> Here are instructions on resizing the Wubi filesystem. (Search for resizeroot): [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

The only snag is, you'll need room to install the lvpm package...

Maybe if you can purge some non-essential packages, you could make room?

Maybe open a terminal (Applications>Accessories>Terminal) and type
```

sudo apt-get clean all
```This will clean out /var/cache/apt/archives and /var/cache/apt/archives/partial.

The clean all code worked very well and opened up a 100MB of space.

I uninstalled all the unnecessary software. But that is besides the point.

For now, I'll stick to what I have. Ubuntu is working fine and on the very basic level, I really don't need the apps I'm trying to install :D

Thanks to all of you for the help! Never thought help would come this fast. The Ubuntu community rocks! Expect me to install Ubuntu right after I get a new laptop which should have more space on the hard drive :P

---

