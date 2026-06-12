---
title: "cannot see second internal hard drive"
date: 2009-03-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lariconda on 2009-03-23
Hello, I was hoping someone can help me with a problem I am having..A little background first. I am running xubuntu 8.10 on my dell pc and have been for a few months now and really love it, but this problem has me wanting to pull out my hair. I have two internal hard drives a 20 gig and a 30 gig, so I figured I would put the os on my 20 gig and keep my media on my 30 gig. I have followed all previous posts in regards to this problem to no avail. I cannot get xubuntu to see my 30 gig that I have all my media stored on. Please help...going nuts here without my media... sorry I should have mentioned the media was put on there with my xubuntu machine. Detailed instruction for this newbie would be very helpful as I am new to the linnux community.

---

### Post by lariconda on 2009-03-23
Angry  cannot see second internal hard drive
Hello, I was hoping someone can help me with a problem I am having..A little background first. I am running xubuntu 8.10 on my dell pc and have been for a few months now and really love it, but this problem has me wanting to pull out my hair. I have two internal hard drives a 20 gig and a 30 gig, so I figured I would put the os on my 20 gig and keep my media on my 30 gig. I have followed all previous posts in regards to this problem to no avail. I cannot get xubuntu to see my 30 gig that I have all my media stored on. Please help...going nuts here without my media... sorry I should have mentioned the media was put on there with my xubuntu machine. Detailed instruction for this newbie would be very helpful as I am new to the linnux community.

---

### Post by anjilslaire on 2009-03-23
Hi there.
First, getting angry and double posting within a few minutes will not solve your problem.

However, there are a few steps you need to do to get a 2nd internal drive visible. Try the following:

[http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/)

---

### Post by lariconda on 2009-03-23
Sorry for the double post, it's my first time posting in the forum. Thank you for the link but I still have a few ?'s. First the article assumes too much... I&#8217;m also going to assume that you knew how to make it a master or slave, you&#8217;ve checked to make sure that it shows up in bios, and that it was intalled properly. It also assumes you&#8217;ve already formatted your drive in linux ext3 format, using a tool like gParted, or something similar. I don't know how to check if it shows up in bios. Anyway this is what my terminal reads.

larry@larry-desktop:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00023b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3493    28057491   83  Linux
/dev/sdb2            3494        3649     1253070    5  Extended
/dev/sdb5            3494        3649     1253038+  82  Linux swap / Solaris
larry@larry-desktop:~$ 

Is it seeing both my hard drives? Can you tell from this screen if they are mounted? 

The article say it should look something like this...

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 4678 37576003+ 83 Linux
/dev/hda2 4679 4865 1502077+ 5 Extended
/dev/hda5 4679 4865 1502046 82 Linux swap / Solaris

Notice mine says sda and sdb article says it should read hda

---

### Post by ugm6hr on 2009-03-23
> **lariconda said:**
> sorry I should have mentioned the media was put on there with my xubuntu machine. 

If you wrote to the HD from Xubuntu, it must have been mounted.

Don't worry that it says sda / sdb - this is correct for SATA drives.

Your "media" drive is sdb.

Unfortunately, the way that the drive is structured looks like you tried to install Ubuntu on it.  So I have a suspicion that you have probably wiped it at some point.

You can check if it is mounted already with:
```
df -h
```

This will help you automount it:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by lariconda on 2009-03-23
This is what happened when I entered df-h code:

larry@larry-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              18G  2.5G   15G  15% /
tmpfs                 504M     0  504M   0% /lib/init/rw
varrun                504M  108K  504M   1% /var/run
varlock               504M     0  504M   0% /var/lock
udev                  504M  2.8M  502M   1% /dev
tmpfs                 504M     0  504M   0% /dev/shm
lrm                   504M  2.0M  502M   1% /lib/modules/2.6.27-11-generic/volatile
larry@larry-desktop:~$ 

So to me it looks like it sees it but hasn't mounted it?

---

