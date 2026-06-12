---
title: "Problems mounting partitions on live CD"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Rhapsody on 2006-09-02
Recently, I had a rather severe problem with my root partition filling up entirely. Rather than attempting to fix this, I've decided to wipe most of my partitions and start from scratch.

My plan for this entails using an Ubuntu Live CD (with GParted on it) to shuffle around an NTFS partition until I end up with an ext3 partition (with the same data on it) taking up the space. I then backup any data I want to keep from my other partitions on to it, and wipe out almost everything to make way for a new Kubuntu install.

Problem is, the live CD refused to mount most of my partitions. Attempting to moutnt my root, /home, or Windows FAT32 partitions produced errors about them not being removable drives (???) and GParted just got stuck scanning drives indefinitely and wouldn't start.

This has me completely stuck, as (at the very least) I will need to use GParted and copy the data from my /home partition on to the new ext3 partition I will create with it (meaning I'll need to mount /home).

I'm pretty eager to get on with this, but I don't want to lose my data either. This is the method by which I intend to save it, but it doesn't seem to be working so far.

---

### Post by Rhapsody on 2006-09-02
I went back into the live CD to get some specifics.

Going into 'Places', 'Computer' and attempting to access any of my partitions results in an "Unable to mount the selected volume" error. Under 'Further details', I get "error: device [etc] is not removable" and "error: could not execute pmount".

GParted simply gets stuck at "Scanning all devices..." and after some CD and HD activity, nothing happens.

---

