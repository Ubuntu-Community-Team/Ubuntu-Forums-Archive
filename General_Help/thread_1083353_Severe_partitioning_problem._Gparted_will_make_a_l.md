---
title: "Severe partitioning problem. Gparted will make a lot of useless adjustments"
date: 2009-02-28
forum: General Help
---

### Post by wersdaluv on 2009-02-28
I want to have an extra partition for another OS. To do that, I resized my 113gb /home partition, moved my / partition, copied and pasted my vista partition to a new secondary partition, and created the new partition on the empty space in the middle of the partitions. I know that this is going to take a hell lot a time but not as much as I thought. 

I am on the Intrepid Live CD. In order to achieve my desired partitioning, I moved, resized, and copied my partitions for a few times on gparted. I never thought that gparted would take every step that I made to achieve the partition. It would resize my 113gb /home partition thrice, move all my partitions for a number of times, copy my partition for a number of times, etc. Now, gparted will make 27 major operations and I can't stop it because it will cause severe damage. 

Yes, I backed my most important data up but I still dont want to wipe out more than a hundred gb of data. I just backed up about 10gb of important data. On the other hand, I fear having problems with my hard drive because it's going to do this partitioning thing all day and after all those efforts, I still might lose some of my data.

Waaaaaaa! What can I do??

---

### Post by thtrgremlin on 2009-02-28
If it has already started, then you may just need to sleep on it and wait for it to finish. Something I learned the hard way is that gparted is just a GUI. Each change you select causes it to write the equivalent command to a script. When you tell it to "go" it runs the script. A good thing and bad thing is that it does not try to optimize the script, or try to do it some other better way. It just does what you told it to do, not find the best way to make it look like the end result. This gives you more power and control... but as you saw, it has its side effects.

What I learned to do is make all the changes then look at the end result as well as the "detailed" view, which is basically the script. I try to see if there is a better, faster way to do everything, then cancel all changes, start over, and do id right.

I will agree, from experience that while expanding or shrinking partitions are quick, moving the beginning of a partition can take a VERY long time. If you moved a partition, then decided to move it a little move, it is going to do BOTH operations. So tweak with how you want it to look, start over, and do as FEW steps as possible to reduce time.

I feel your pain, but you may just have to wait this out and remember for next time.

Best luck.

---

### Post by wersdaluv on 2009-02-28
It has completed one of 27 operations now and that is shrinking my /home partition from 113 to 101gb. After that, it will move it again to 100gb. 

Thanks for the explanation. I never saw it that way.

However, do you think, it is advisable to wait for this to finish? Doing a lot of partition operations, I presume, is prone to errors. What do you think? Is there a right time to cancel this? 

The first three operations are to shrink my home partition then the next operations involve my root and Vista partitions. Can I just cancel this operation after the first three operations to save my home partition? It's fine for me to have problems with my other partitions just to save my /home.

---

### Post by wersdaluv on 2009-02-28
Okay. I cancelled the operation after resizing my /home!!!! Woohoo. And guess what, my partitions are still alive!

---

### Post by wersdaluv on 2009-02-28
Words of the wise: it's best to apply one partitioning change at a time. 

That's what I'm doing now. :)

---

### Post by -kg- on 2009-02-28
If it were me, I would take thtrgremlin's suggestion, sleep on it, and let all the operations complete.  There is more to screw up than just the partitions; you could quite possibly screw up the partition table in the MBR section.

I'm not sure, but I think there are ways (and software) to recover data from such partitions, but it should be able to be done if letting the operations complete screw it up anyway.  It's very likely you will have to if you interrupt the partitioning operations early.  I'm not sure at what point(s) the partition table is updated during multiple partitioning operations, but early interruption may corrupt it.

The best idea for backups is to back up all the partitions...the whole partition...before performing such an operation.  Then, if it screws up, you have all your partitions backed up, can erase them all on your main hard drive, recreate them, and load the images back on them.

Let it all complete is my suggestion.

<edit> Well, I guess my suggestion is redundant.  I'm certainly glad to hear that you were successful.

---

### Post by thtrgremlin on 2009-02-28
It it is taking many many hours to complete 1 of 27 steps, and all your important data is backed up, then it can be FASTER to loose the whole disk, reformat it, and start over. There are also differences between hitting cancel in gparted, and hard restarting the computer in the middle of a move.

I will totally agree that it is cautious, and takes barely any time to do one operation, apply it, then do the nexd rather than setting of many things in a querry(sp?).

Sounds like this has been a good learning experience  :) Happy to hear there is no apparent damage.

---

### Post by wersdaluv on 2009-03-01
After that, because of my lack of patience and stubborness, the live CD session hung while I was moving my root partition. I ended up forcing my laptop to reboot so I lost my root partition. When I was moving my Vista partition, my lack of patience striked back. I decided to delete it and just reinstall Vista. LMAO!

---

### Post by thtrgremlin on 2009-03-01
we all mourn for you

Personally, having a lot of disk storage myself, always consider how much faster a fresh install can be over moving a partition. I once backed of part of, and shuffled around 2TB of data once (I can't even remember why) and it took 3 days to complete all the operations. (I had written my own script though, not used the gui) Everything went perfectly, aside from loosing my computer for 3 days. All I could wonder afterwards was, was it really worth it?

Either way, i'll (hopefully) never do that again if there is any way to avoid it.

---

### Post by wersdaluv on 2009-03-02
Aw! That's a humongous hd. We better backup our important data from time to time. I'm buying an external hard drive.

---

