---
title: "Partition question"
date: 2009-03-27
forum: General Help
---

### Post by getintanked on 2009-03-27
I have a laptop where I installed hardy on 25 gigs of my 120 gig hard drive. The rest I put to a windows partition.

Now, I'm ready to eliminate windows and give my linux partition all the hard drive space.

How would I go about this without formatting the harddrive?


Thx!
-Matt

---

### Post by kanikilu on 2009-03-27
You can't resize the Ubuntu partition while it's mounted, so the easiest thing is to use gparted in the Ubuntu Live CD, or the GParted Live CD to delete the Windows partition and then resize the Ubuntu partition.

This can take quite a while. It should do this non-destructively, but it's always a good idea to backup anything of value before changing the partitions.

---

### Post by 3startuna on 2009-03-27
> **getintanked said:**
> I have a laptop where I installed hardy on 25 gigs of my 120 gig hard drive. The rest I put to a windows partition.

Now, I'm ready to eliminate windows and give my linux partition all the hard drive space.

How would I go about this without formatting the harddrive?


Thx!
-Matt

kanikilu is right!

You can only perform a partion operation using gparted on a drive that's unmounted. 

Gparted wont allow you to unmount the drive the OS is running on for obvious reasons.

To do this you will have to run live CD or boot from a USB drive. then delete the partition you dont want and change "space before" partition value to 0. (assuming the ubuntu partition isnt the first one on the disk)

Then the entire drive will be ubuntu,  

hope this helps

---

### Post by getintanked on 2009-03-27
Okay cool. 

I'm downloading gparted live-cd iso as I type. I'll post back with questions and updates.

Thanks, you guys rock.
-Matt

---

### Post by getintanked on 2009-03-27
Gparted for the win. :)

Worked like a charm - didn't take that long, it just has to move whatever partition you had originally to the front of the drive. So the more you have the longer it would take.
In my case i only had 20 gigs to move.

Thanks again.
Closed.

---

### Post by 3startuna on 2009-03-28
congrats man. :)

---

