---
title: "Power surge in the middle of GParted operation!"
date: 2009-03-01
forum: General Help
---

### Post by kahlil88 on 2009-03-01
If I wasn't irritated enough knowing I had to wait 18 hours to grow my Home partition (to the left, I'm an idiot), there was a power surge about 8 hours into the operation! I can mount the partition, but there is a lot of missing data. I was trying to grow the partition from 261 GB to 444 GB, and GParted shows a 261 GB partition with 183 GB unallocated. Is possible to somehow make it resume from where it was killed off, or could I maybe expand it the rest of the way to the right and run PhotoRec or something to recover my files?

---

### Post by arepaking on 2009-03-01
Hello,
Moving or Resizing partitions is a very delicate procedure. If I were you I would do the whole process again. You don't want to take chances and figure it out later that some disk sectors were not properly moved.

Quick Question, after the power failure were you able to see the whole disk capacity again?

---

### Post by kahlil88 on 2009-03-01
GParted sees it as a 261.17 GB partition, but it shows up in Places as 280.4 GB Media. I think all of my Documents and Pictures are safe, but my Music folder is missing data and my Videos folder isn't there at all. Disk properties shows it as 257.1 GB with 176.9 GB used, but the contents field reads as 10,855 items, totalling 49.7 GB.

---

### Post by kahlil88 on 2009-03-01
So what's the best solution? I don't see how it would be possible to start the operation over, as my Home partition has already been moved to the left, but is simply missing lots of data. Should I expand it the rest of the way to the right and run PhotoRec, or would this somehow make recovering the missing data more difficult?

---

