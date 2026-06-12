---
title: "delete swap file?"
date: 2009-03-05
forum: General Help
---

### Post by sansa dude on 2009-03-05
ive been reading around and i understand there is a 1gb swap file when you are using ubuntu. is there a  way for me to delete this? i  really need to conserve on my hard disk space so this woul help alot!

---

### Post by lykwydchykyn on 2009-03-05
I'm not sure that's entirely accurate.  You can see what files or partitions are being used for swap with this command:
```

cat /proc/swaps

```
Post the output from that and we'll go from there.

---

### Post by sansa dude on 2009-03-05
yea i wasn't quite sure about it but i  thought it took up somem space and isnt used so i wanted to see if it can  be removed but
> Filename				Type		Size	Used	Priority
/dev/sda5                               partition	465844	134376	-1


thats the output if it matters im on a 10gb hard drive

---

### Post by Nano_ext3 on 2009-03-05
I could be wrong, I dont believe there is a default swap specified on a fresh install.  Im pretty sure you have to specify a swap file while installing Ubuntu.  Swap is really only necessary for older machines, such as mine, where I have 1 gig of ram and a slow processor.  In typical fashion I made my swap twice the size of my RAM, so it was made to be 2048 MB.  Removing a swap is not too dangerous, but may I ask why you really want that space, are you that* low?  Last time I went hunting for large files, I got overzealous and ended up with some broken packages. 

Be Careful, this isnt windows, add/remove programs cant save you here :)

Cheers!

-Nano

---

### Post by sansa dude on 2009-03-05
ok if it  seems to risky then i probably shouldn't do it i am on a fairly old laptop with 256mb of RAM 10gb hard drive  and a pentium 3 processor and my CPU speed is i think 700 MhZ so i think ill leave it be.

---

### Post by lykwydchykyn on 2009-03-05
You are best of leaving it with that little RAM.  It's only 465 MB according to your file, and it's on a separate partition, which means deleting it would mean restructuring your paritions (messy and potentially fatal).

---

### Post by jgoguen on 2009-03-06
Agreed, with that little RAM you should actually have a swap partition of at least twice your RAM size.  Since you have 256MB RAM, your swap partition should be at least 512MB, and it's currently less than that (~455MB).  Your best bet is to leave it as-is honestly.  Swap is surprisingly important too, but that becomes less true as RAM goes up depending on your usage.  As one forum user's signature says...
> Running without swap is like skydiving without a reserve chute.  You probably won't need it, but if you do...

---

### Post by lykwydchykyn on 2009-03-06
> **jgoguen said:**
> Agreed, with that little RAM you should actually have a swap partition of at least twice your RAM size.  Since you have 256MB RAM, your swap partition should be at least 512MB, and it's currently less than that (~455MB).  Your best bet is to leave it as-is honestly.  Swap is surprisingly important too, but that becomes less true as RAM goes up depending on your usage.  As one forum user's signature says...

My guess is that the video card is sharing some RAM, probably 32 MB, which would leave the system ram at 224.  So the automated partitioning would have made the swap 2 * 224 = 448.  Throw in the mass confusion of Megabyte to Mebibyte measurements, and you've got whatever the swap amount ended up being.

---

### Post by jgoguen on 2009-03-06
Ahh yes, I totally forgot about shared video memory :)  And you're right, the conversion differences in 1MB on a hard disk vs. 1MB in RAM (which annoys me to no end, and I always forget about) make perfect sense to give us that odd swap size.

---

