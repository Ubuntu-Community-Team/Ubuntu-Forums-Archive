---
title: "How Do I Create Separate /home During Install?"
date: 2009-03-26
forum: General Help
---

### Post by Ms_Angel_D on 2009-03-26
I have found all kinds of tutorials on how to create a separate /home after Ubuntu is installed but How do I do it during the setup process?

Thanks,
Angel

---

### Post by xodus1 on 2009-03-26
While formating make your root and swap (whatever size desired for root and about 2gig for swap) 3 partition (again size desired very large) name it /home and that should do it 

Also at this time if you see any other partition (ie windows) go ahead and name it before formatting (example /vista)

---

### Post by Ms_Angel_D on 2009-03-26
So I have to format prior to running the install?

---

### Post by jelle_ on 2009-03-26
while running the setup, choose the expert option when it asks you about partitioning. then you make tree partitions, one mounted at /, one at /home and a swap

---

### Post by xodus1 on 2009-03-26
Yes if you want it to work effortlessly just backup what you want to keep to a separate partition, flashdrive, etc. Fresh install new partition (don't format any other partition just root, swap, and home

---

### Post by Merk42 on 2009-03-26
You don't have to format prior to install, the install process will do the formatting.

Just so it doesn't confuse you, jelle_ means **three** partitions.

If you're wondering about size, my / partition is about 16GB, but I've only used a little more than 4GB.

---

### Post by Ms_Angel_D on 2009-03-26
Ok guys thanks a bunch I think I get it now :D

---

### Post by c/Kr3t on 2009-05-12
i think it's like this

boot from your live CD and choose to install ubuntu, obviously. when you get to the part  in the installer where you prepare disk space, choose manual. from there you'll see all your partitions laid out.

now what i'm going to do, i'm doing it as i type this out, is edit the free space i have to about 7 gigs, primary, ext3 formatted and the mount point is going to be /home.

then i'm going to make a 1677 size swap  and then all the rest will be on /.

i think that should do it. i'll post back if it's correct or not

---

### Post by c/Kr3t on 2009-05-12
yes, that way worked.  didn't have any troubles. i even made a sandwich  :D

---

### Post by Ms_Angel_D on 2009-05-12
wow this thread is old...lol. Thanks for your input Kr3t hopefully this will help somebody else, as I figured it out a while ago ;)

---

### Post by c/Kr3t on 2009-05-12
heh, ya. i figured as much by the date of the posts.

---

