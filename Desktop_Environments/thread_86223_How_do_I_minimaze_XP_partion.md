---
title: "How do I minimaze XP partion?"
date: 2005-11-04
forum: Desktop Environments
---

### Post by bengtfalke on 2005-11-04
I have installed Breeze alongside with XP onm my portable. Now I would like to shrink and minimize the XP partition and expand the Breeze partition. What is the easiest way to do that.

I have GRUB for chosing startup OS...

regards/falke

---

### Post by Kyral on 2005-11-04
GParted anyone?

But BE CAREFUL. Things can get sketchy. Windows won't care if you shrink it, but be careful with the Breezy partition. Linux partitions prefer to have thier ending points changed rather than their starting points, if that makes any sense

---

### Post by aysiu on 2005-11-04
I believe you may also want to defragment your XP partition before you shrink it.

Oh, and back up everything before doing any repartitioning! Just in case.

---

### Post by magnusbb on 2005-11-04
I really don't recommend it. I shrank my XP partition (NTFS) in Windows using Partition Magic. That is a reliable program, in my opinion, and that part of the process is not dangerous.

But when I was to resize the ReiserFS partition using GParted (from the Ubuntu live-CD), I ended up corrupting the whole partition. I tried to run the "reiserfsck" check on it, but that didn't work either.

---

### Post by bengtfalke on 2005-11-04
What shall I do then?  Delete my XP partion all together or? How do I remove GRUB then?

regards/falke

P.S. I just love Streamtuner/Streamripper and amaroK.... they are arguments enough for switching to Linux and Breeze..... D.S.

---

