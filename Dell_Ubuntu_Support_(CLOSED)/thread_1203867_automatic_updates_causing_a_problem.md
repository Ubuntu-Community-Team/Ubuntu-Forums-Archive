---
title: "automatic updates causing a problem"
date: 2009-07-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by billyjack on 2009-07-03
I have been on and off with Dell.. my mini 9 ubuntu 8.10 had to be reloaded and it comes up with 340 updates.. Dell tells me not to download them because it will fill up the memory and so what should I do about that?  They seem to be no help at all.  Sorry to ask on a holiday, but no help from Dell.

Thanks

---

### Post by Boondoklife on 2009-07-04
Ok are you saying updating will fill up your hard drive? How much space do you have?

---

### Post by billyjack on 2009-07-04
1GB DDR@ 533MHZ 1 Dimm  ,  it already shut down once and they told me to reload Ubuntu.  I did that and now it is coming on again saying I have all of these updates.  When I talk to them they said you dont have to download them, because it doenst need them.. but I would rather ask people that are familiar with ubuntu.

Dell also said I could download these updates to an external drive.. but I am not familiar in how to do that.. do you have any suggestions?

Would downloading another version of Ubuntu be the better thing to do?

Thanks

---

### Post by Boondoklife on 2009-07-04
How much hard drive space do you have, what you quoted is your RAM =P

When it comes to updates, chances are you do want it, especially security updates. As far as upgrading to a newer version, you can but the adage comes to mind, If it isn't broke don't fix it.

But if you do decide to upgrade then please make a back up of your data first just in case.

---

### Post by billyjack on 2009-07-04
Sorry about that.. 4GB Solid State Drive (mini card module pata

---

### Post by Boondoklife on 2009-07-04
Ahh well that is kinda tight, My install of 9.04 takes up 3.3G and that is just the OS and apps. Let see how much space you have free. Open a terminal and run this, post the results here.
```
df -h
```

---

### Post by billyjack on 2009-07-04
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             3.4G  2.9G  381M  89% /
varrun                501M  104K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   44K  501M   1% /dev
devshm                501M     0  501M   0% /dev/shm
lrm                   501M  1.9M  499M   1% /lib/modules/2.6.24-24-lpia/volatile
gvfs-fuse-daemon      3.4G  2.9G  381M  89% /home/george/.gvfs

---

### Post by billyjack on 2009-07-04
Is that what you needed?

---

### Post by Boondoklife on 2009-07-04
Yea you are going to be cutting it very close with that, Here is the size of your drive 3.4G, I dont know about the netbooks but I know with laptops and pc's they normaly have hidden partitions eating up space that you dont know about.

One option would be to try gparted and see if there are any such partitions. If there are then you could try removing then and reinstalling to get that extra space.

Either way to be honest 4G is not much and I really hate to say it but ya might want to look into a bigger drive.

---

### Post by billyjack on 2009-07-04
Is there a way to download the updates to the outside drive?

---

### Post by Boondoklife on 2009-07-04
well you could mount an external drive and then copy all the data from /var/cache to it, then unmount it and remount it on the /var/cache directory. But this may not resolve the issue as you will need to INSTALL said updates which will goto various places on the drive.

Try going into synaptic and under prefs there is an option to delete downloaded packages, check that and see if it helps.

---

### Post by anjilslaire on 2009-07-04
The Dell version of Ubuntu has problems like this, since they tend to release updates in huge batches like this.
I recommend installing the latest Ubuntu 9.04 Netbook Remix. It's designed for small drives in netbooks specifically and may give you a bit more room.
After installing, open Synaptic and navigate to 
Settings > Preferences > Files, and select "Delete downloaded packages after installation." This will prevent updates from hogging too much space after install.

Also, until it gets updated fully, de-select a bunch of the updates it offers, so that you're only installing ~100 or so at a time, so you don't fill the drive up. After installation, re-run Synaptic, check for updates, select 100 again, and repeat.

After you're finally updated, you won't see such massive downloads at any one time.

There are more threads on this topic in this forum as well; you're not alone in having a 4gig drive.
I have a 32gig drive, but even an 8gig would resolve the issue. But, you can manage on the 4gig if needed.
Let us know how it goes.

---

