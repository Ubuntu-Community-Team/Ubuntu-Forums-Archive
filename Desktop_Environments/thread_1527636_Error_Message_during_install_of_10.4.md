---
title: "Error Message during install of 10.4"
date: 2010-07-09
forum: Desktop Environments
---

### Post by boyblue42 on 2010-07-09
I recieve an error mesage during install of ubuntu 10.4 while partitioning ext3 freezes at 5% then a black screen  i see the cursor but can't move it with the error message "process:304): Glib - warning **: getpwuid_r() : Failed due to unknown user id (0)" , i have tried installing 9.10  and 5.0.5 Debian when i installed 9.10 ubuntu and debian it just froze and wouldn't do anything. what is causing this and how can i fix it?

---

### Post by gordintoronto on 2010-07-09
Tell us about the computer. How much memory? How much hard drive space? What partitions did you create?

There are many, many things which might cause the problem. For example, I once accidentally specified a 1MB swap partition, and the install died about the same place yours did -- but I doubt if that is your problem.

---

### Post by boyblue42 on 2010-07-09
it is a hp pavilion a1620n western digital 250gb hard drive, ATI Radeon 256 mb, 1.5 gb PC2 Ram, have tried everyway imaginable to partition from just partitioning it with only ubuntu using largest contigious space and reformatting the entire drive, and partitioning it manually many times can't even get it to reformat it freezes at ext3 during partition no matter how i do it.

---

### Post by gordintoronto on 2010-07-09
If partitioning is the problem, you could try downloading "partition magic" which runs from its own LiveCD. Did you specify "mount points," for root and home, or just root if you only choose one partition.

---

### Post by boyblue42 on 2010-07-10
how do i run partition magic? i don't have another operating system installed, when i ran partitioning by itself it froze as well

---

