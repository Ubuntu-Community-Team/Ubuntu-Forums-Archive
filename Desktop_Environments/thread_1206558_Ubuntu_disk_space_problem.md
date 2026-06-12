---
title: "Ubuntu disk space problem"
date: 2009-07-07
forum: Desktop Environments
---

### Post by TBTsjG89 on 2009-07-07
I have Ubuntu installed on a 16 GB ext4 partition. I recently noticed that it was almost full, even though I keep most of my stuff on an other disk. Is this possible?
According to (sudo) nautilus:
(Only folders in / above 100 MB)
**/home** - **192 MB**
**/lib** - **140 MB**
**/lib64** (symbolic) - **140 MB** 
**/sys** - **584 MB**
**/usr** - **2.5 GB**
**/var** - **591 MB**
And **2.8 GB** of free space
Is it being ignorant to ask where the rest of the space is?
If not:
   Where is the rest of the disk space?

thanks in advance

mr. krey

---

### Post by jerrrys on 2009-07-07
in terminal  [B]df -Th
[/B]
may give you an answer

---

### Post by shad0w_walker on 2009-07-07
Assuming you're using gnome (standard Ubuntu) then you can go to  Programs > Accessories > Disk usage analyser

That should show you all the space consuming things.

---

### Post by TBTsjG89 on 2009-07-07
Thanks very much! *df -Th* didn't help me, but Disk usage analyser told me there's 8 GB of hidden files in /home
So it seems nautilus doesn't add hidden files when it calculates the "size" of a directory. Bug or feature?

---

### Post by taurus on 2009-07-07
Don't forget to empty your trash bin to free up the space.

---

