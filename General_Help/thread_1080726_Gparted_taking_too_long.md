---
title: "Gparted taking too long?"
date: 2009-02-25
forum: General Help
---

### Post by gamewizz on 2009-02-25
On Monday around 3 pm i starting a resizing on my main partition to take up some empty space (237gb into 297gb). well now its about 48 hours later and its not done. this morning it STARTED AGAIN!! Im not sure if this is a different process for the resizing but its getting old. When i started the estimated time was ~9.5 hours, and now im going into the 3rd day   anyone know if this is normal? should i just wait it out or should i stop it? any help would be greatly appreciated!!!

[[IMG]http://img528.imageshack.us/img528/3273/gpartedprob1.th.jpg[/IMG]](http://img528.imageshack.us/my.php?image=gpartedprob1.jpg)

(sorry about the quality)

---

### Post by ibuclaw on 2009-02-25
Hmm... I have never resized an **entire** 250GB filesystem before, but I know that 50-60GBs can take upto 3-4 hours.

Regards
Iain

---

### Post by gamewizz on 2009-02-25
I understand that 290 gigs would take a long time, but 2+ days!? and why did it "restart"?

---

### Post by gamewizz on 2009-02-25
bump

---

### Post by wangsuda on 2009-02-25
> **gamewizz said:**
> On Monday around 3 pm i starting a resizing on my main partition to take up some empty space (237gb into 297gb). well now its about 48 hours later and its not done. this morning it STARTED AGAIN!! Im not sure if this is a different process for the resizing but its getting old. When i started the estimated time was ~9.5 hours, and now im going into the 3rd day   anyone know if this is normal? should i just wait it out or should i stop it? any help would be greatly appreciated!!!

[[IMG]http://img528.imageshack.us/img528/3273/gpartedprob1.th.jpg[/IMG]](http://img528.imageshack.us/my.php?image=gpartedprob1.jpg)

(sorry about the quality)

This is not normal. I have reformatted and repartitioned 300gig hard drives in 20 minutes, using gparted with ubuntu 8.10. Something may be physically wrong with your disk (hazarding a guess).

---

### Post by gamewizz on 2009-02-25
hmm, is it safe to stop it? so i can run more error checks or use another program?

---

### Post by ibuclaw on 2009-02-25
In a normal situation, I would say "**no**", as stopping gparted halfway through a task can potentially (or, more bluntly, **will**) harm the filesystem it is performing an operation on.

But, considering the current special situation, I don't know.

If you have data already on the filesystem you are resizing, I would love to say that everything is fine, but I agree with wangsuda, I've never seen this happen before so I can not really comment further.

But, if you are willing to take that risk... you may be having to clean up any damage done either way.

Regards
Iain

---

### Post by dkulchenko on 2009-02-25
If it's copying right now, **don't** stop it. It will ruin your filesystem. It took my computer 3 hours to resize 120GB, so I'm guessing about 7 hours for 250GB. If you go to details, and it is on "resizing filesystem", it might not be doing anything (it WAS safe to cancel in my situation), but if it's not, let it do its thing.

---

### Post by gamewizz on 2009-02-25
> **dkulchenko said:**
> If it's copying right now, **don't** stop it. It will ruin your filesystem. It took my computer 3 hours to resize 120GB, so I'm guessing about 7 hours for 250GB. If you go to details, and it is on "resizing filesystem", it might not be doing anything (it WAS safe to cancel in my situation), but if it's not, let it do its thing.


Its on "perform real move"

---

### Post by dkulchenko on 2009-02-25
If it's been on "performing real move" for more than 24 hours, something is seriously wrong. If not, you should leave it and come back in a few hours.

---

### Post by gamewizz on 2009-02-25
> **dkulchenko said:**
> If it's been on "performing real move" for more than 24 hours, something is seriously wrong. If not, you should leave it and come back in a few hours.

i think its been on "performing real move" since 7am today (about 13 hours ago), and its maybe 1/4 done.

---

### Post by dkulchenko on 2009-02-25
Well, if the progress bar is moving, and it's visibly doing something, then leave it. You should only start to worry when it's working, but does not seem to be doing anything.

---

### Post by gamewizz on 2009-02-25
> **dkulchenko said:**
> Well, if the progress bar is moving, and it's visibly doing something, then leave it. You should only start to worry when it's working, but does not seem to be doing anything.

yea i can see it moving, just VERRRRRY slowly. at this rate it might be done by tomorrow night. is this the last step or is there more?

---

### Post by dkulchenko on 2009-02-25
You should be able to see if it is the last step or not by the details window. If there are no more operations pending, then yes, this is the last step.

---

### Post by gamewizz on 2009-02-25
great!! thank you so much for your help!

---

### Post by louieb on 2009-02-25
Just wondering are you trying to grow it to the left ( will be very slow) or to the right (should not take more that an hour - probably a lot less).

---

### Post by gamewizz on 2009-02-25
to the right i think, i had ~56gb of free space that i want to add on to my main partition. Im increasing the size of the main partition from 236gb to 296gb.

---

### Post by kahlil88 on 2009-02-28
I'm also in the middle of a dreadfully slow operation. My goal was to create a separate Home partition, so I resized my system partition and created a new one (260 GB) for all of my data. I spent roughly 2 hours moving my files over, then resized my Home partition to the left. It spent over an hour on the read test, but now that it's performing the real move, it's showing an estimated time of 18 hours. I'm growing the Home partition from 260 to 444 GB, but there's really only 200 GB of actual data. When it gets past the real data, will it at least speed up or be safe to cancel?

---

### Post by adult swim on 2009-03-01
i moved some partitions around once on an 80gb hard drive.  i moved some to the left and some to the right.  it took over a day and a half for it to finish.  i learned to never move left!

---

### Post by kahlil88 on 2009-03-01
> **adult swim said:**
> i moved some partitions around once on an 80gb hard drive.  i moved some to the left and some to the right.  it took over a day and a half for it to finish.  i learned to never move left!
RAmen to that! I could have saved myself hours moving 10GB of operating system data to a separate partition instead. But I don't see why resizing has to involve moving the entire filesystem. I just wanted to add free space to my partition.

---

### Post by -kg- on 2009-03-01
> **kahlil88 said:**
> RAmen to that! I could have saved myself hours moving 10GB of operating system data to a separate partition instead. But I don't see why resizing has to involve moving the entire filesystem. I just wanted to add free space to my partition.

Well, you resized it to the left.  Most of the system files will reside on the left side of the partition, so when resizing it in that direction, it will move all the files there to the left so they remain to the left side of the partition.

That's why, if at all possible, you always want to resize or move the right side of the partition (AFTER defragging and, if possible, consolidating folders and files, if it's a Windows partition!).  There will be few if any files present there, and a lot less likely that any files will have to be moved.  And if any files must be moved, there will be few of them.  It will take a lot less time.

---

