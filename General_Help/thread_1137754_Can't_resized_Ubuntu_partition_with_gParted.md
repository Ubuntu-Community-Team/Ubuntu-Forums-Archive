---
title: "Can't resized Ubuntu partition with gParted"
date: 2009-04-25
forum: General Help
---

### Post by happinesskills on 2009-04-25
I just deleted my old Vista partition (god I hate vista) & I was hoping to add the new unallocated space onto my Ubuntu partition, but it won't let me. (see attachment).

I have Ubuntu Intrepid Ibex

---

### Post by Tim Sharitt on 2009-04-26
I'm not sure if this is still the case, but in an older version of gparted, the partition could only be resized to the "right" (as viewed in gparted). 

In order to add free space located on the "left" side, the partition needs to be moved over to occupy the free space, then resized from the "right" side.

---

### Post by happinesskills on 2009-04-27
well how do I do that?

---

### Post by lindsay7 on 2009-04-27
Are you sure that your Ubuntu partition is UNMOUNTED?

---

### Post by tubbygweilo on 2009-04-27
happinesskills,
I came across this well illustrated [Gparted]("http://www.dedoimedo.com/computers/gparted.html") guide a couple of days ago and have passed it to others with good results. The example seen as task 1 shows resizing of an unmounted partition and shows the left / right resize move options offered by the left right sliders.  

I hope this helps with your problem.

---

### Post by happinesskills on 2009-04-27
I have 2 ubuntu installs, but is broken (the smaller one) & I want to add the 49GB of unallocated space onto my bigger (& working) ubuntu partition.

But surely, if I unmount it, my computer will crash. won't it?

PS: I can't resize/move the Ubuntu partition because the Resize/Move button is disabled.

---

### Post by dearingj on 2009-04-27
What you want to do, I believe, is boot from a live CD and run GParted. That way the partition you're trying to resize won't be mounted.

---

### Post by happinesskills on 2009-04-27
That makes sense, but my Live CD has Hardy & I'm running Intrepid. Would that have problems?

---

### Post by Tim Sharitt on 2009-04-27
Using the Hardy live CD should make no difference.

---

### Post by lindsay7 on 2009-04-28
Things will go a lot cleaner if you download Gparted from their web site. It will be an ISO download and will start up your computer and you can do your resizing from there. Doing it this way is easier and takes any confusion out of the process. The Gparted live disk is good to have around anyway.

---

