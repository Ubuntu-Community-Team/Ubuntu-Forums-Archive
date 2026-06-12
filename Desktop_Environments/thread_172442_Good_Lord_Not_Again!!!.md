---
title: "Good Lord Not Again!!!"
date: 2006-05-08
forum: Desktop Environments
---

### Post by Wr8EYilK8Y on 2006-05-08
As I said in another thread, I've installed 3 times. First install- cool. Second- I still had XP on it and it deleted my Linux partition. Third time- Kubuntu, not Ubuntu. This time? The GParted on my Live CD DELETED EVERY PARTITION ON MY HARD DISK!!!
I have to start again- I tried to reformat freespace, and BOOM it exploded. ](*,) 

Anything I can do to avoid this in the future (a lot of my data is being recovered to burn to CD to be copied after I reinstall)?

---

### Post by glinsvad on 2006-05-08
> ...it deleted my Linux partition
As in, your computer single-handedly decided to delete your partition? Are you completely sure you knew what you were doing?

> Anything I can do to avoid this in the future
Cool down, and think before you act. At some point during the installation you are asked where to install (K)Ubuntu - make sure you select the correct partition. The text mode installer is not that helpfull to a newbie (no offence), so maybe you should try out the graphical installer in the Dapper LiveCD?

---

### Post by Wr8EYilK8Y on 2006-05-09
I was using the Ubuntu Live (Breezy Badger) CD's gparted to partition, yes I knew what I was doing, and yes, instead of formatting freespace, the live CD deleted every partition on the drive... I had to use the installer (text based) to resize one partition, which worked VERY successfully, so I went to format the freespace. I walked away, came back, saw a full 20GB of unpartitioned freespace, and PANICED... I've recovered most of my lost data via google, sourceforge, packages, repositories, and image hosting services, so its no longer as bad as it was.

---

### Post by glinsvad on 2006-05-10
Problem is, you haven't told us exactly what you did - which partitions, which types of filesystems, what actions you took... I'm talking details here.

Hmm, this might sound like I'm joking, but if you can replicate the sequence of events, it would be a prime candidate for a bugreport. You probably don't want to live through the nightmare again, but fixing it might save others from loosing their data in the future...

I couldn't find any previous bugreports resembling what you described, but you might want to browse through them yourself:
[https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=gparted](https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=gparted)

---

### Post by glinsvad on 2006-05-10
Came across the following notes on partitioning in Dapper LiveCD (Flight 7):
> There is a known problem with the partitioner in the live installer which can cause installation failures
[https://lists.ubuntu.com/archives/ubuntu-announce/2006-May/000080.html](https://lists.ubuntu.com/archives/ubuntu-announce/2006-May/000080.html)

Anyway, they are working like crazy to fix these things for the final Dapper...
[https://launchpad.net/distros/ubuntu/dapper/+specs](https://launchpad.net/distros/ubuntu/dapper/+specs)

---

