---
title: "From one HDD to another"
date: 2006-06-08
forum: Desktop Environments
---

### Post by cosine7 on 2006-06-08
I know this might sound wierd, but i just got 6.06 installed on my machine (recent convert) and have been running it happliy now for the last few days, i have decided to keep Ubuntu, but have to keep my XP setup on my other HDD as work codes in VB. Anyway when i installed i chucked on to a spare 40gb drive, but it makes a terrible noise, i have another 80gb (and yes i know, y did'nt i put it thier first). Is it possible to transfer the data from one to another?

---

### Post by frying_fish on 2006-06-08
Yes, you could just blind copy the whole section, if it is a spare partition, could do something like:

dd if=/dev/hdb1 of=/dev/hda2


or something like that assuming the partitions are set up, I'm not sure how windows would like that being done to it, but its a quick shot.

---

### Post by cosine7 on 2006-06-08
i have a spare without windows, just make a swap parttion, or should i just let ubuntu do a bse install then copy over?

---

