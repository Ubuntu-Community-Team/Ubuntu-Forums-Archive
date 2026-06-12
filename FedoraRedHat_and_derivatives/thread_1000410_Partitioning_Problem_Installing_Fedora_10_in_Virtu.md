---
title: "Partitioning Problem Installing Fedora 10 in VirtualBox"
date: 2008-12-02
forum: Fedora/RedHat and derivatives
---

### Post by plinydogg on 2008-12-02
Hi folks,

I'm trying to install Fedora 10 from the LiveCE in a VirtualBox virtual drive. Everything goes fine until it gets to be time to do the partitioning, at which point I get the following error:

"The following errors occurred with your partitioning:

Your /partition is less than 2107 megabytes which is lower than recommended for a normal Fedora install..."

I've got the virtual drive set to 2.6 gigs (i.e., well above the 2107 stated minimum). 

Does anyone have any ideas? Thanks!

---

### Post by plinydogg on 2008-12-02
Sadly, it may be hopeless:

[http://forums.virtualbox.org/viewtopic.php?p=48452#48452](http://forums.virtualbox.org/viewtopic.php?p=48452#48452)

---

### Post by igknighted on 2008-12-03
All you need to do is choose custom partitioning and make the swap partition small enough.  Don't let it set any partition sizes.

But the point about fragmentation is valid.  I wouldn't run a hard drive (or partition) over 75% capacity if at all possible.

---

### Post by plinydogg on 2008-12-03
igknighted: thanks for your input. As I mentioned in the post in the VirtualBox forums, however, I didn't see any option to set the size of the swap partition. But, if you and the other poster think that fragmentation is an issue, I won't mess with it (I thought fragmentation was only a Windows issue though...).. 

If I could just figure out how to get terminal services working right in Ubuntu I could get rid of that Windows partition...maybe I'll look into that....

---

### Post by igknighted on 2008-12-03
> **plinydogg said:**
> igknighted: thanks for your input. As I mentioned in the post in the VirtualBox forums, however, I didn't see any option to set the size of the swap partition. But, if you and the other poster think that fragmentation is an issue, I won't mess with it (I thought fragmentation was only a Windows issue though...).. 

If I could just figure out how to get terminal services working right in Ubuntu I could get rid of that Windows partition...maybe I'll look into that....

Linux does do a much better job avoiding fragmentation under normal circumstances, but when the drive is nearly full, even the best file systems will fragment.  Most say fragmentation will get out of control after a drive has less than 5% free, but I don't like to push it and tend to go with 25% free.  Hard drive space is so cheap now (1TB for less than $100USD), there's no reason to fill drives to capacity.

As for your swap partition, forget that you are making a "swap" partition.  Choose custom partitioning, then create one partition in the virtual drive that is at least 2.1GB as ext3 (or file system of your choice) and use it as /, then create another partition in the rest of the space, and format it as swap.

---

### Post by plinydogg on 2008-12-04
Thanks for the help but I may refrain from doing this if it's going to fragment my drive real bad...

---

### Post by plinydogg on 2008-12-20
Alright, I've since done a fresh install of Ubuntu, intentionally overwriting my Vista partition in the process. I now have sufficient space for the Fedora install in VirtualBox. However, once I install it, I'm not sure how to access it. In other words, if I leave that virtual drive pointing to the LiveCD it boots the LiveCD but if I don't point it towards that CD then it doesn't boot. How does one go about telling the virtual machine to load the newly installed system?

---

