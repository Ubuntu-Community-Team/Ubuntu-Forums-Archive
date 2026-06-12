---
title: "hard drive space?"
date: 2006-02-02
forum: Desktop Environments
---

### Post by dude of wonders on 2006-02-02
cant tell how much space i have left on my hard drive. screenshots down below,
says partition 5 the 9.5 gig free space not available, and partition 1 is showing it iin mib. so i dont know if i have it partitioned correctly or what cause one should show a swap file with like 400mb used and the other should show 9.5 gig, and show how much free space is left for stuff.

so did i mess up on partitioning it or is there a way to fix it so it shows different? 



[IMG]http://i20.photobucket.com/albums/b213/pure_pwnage/Screenshot-2.png[/IMG]

[IMG]http://i20.photobucket.com/albums/b213/pure_pwnage/Screenshot-1.png[/IMG]

[IMG]http://i20.photobucket.com/albums/b213/pure_pwnage/Screenshot.png[/IMG]

sorry about the large images i don't know how to just show them another way

---

### Post by towsonu2003 on 2006-02-02
it looks to me like you forgot to format /dev/hb5. From here: [http://www.tldp.org/HOWTO/Partition/formatting.html](http://www.tldp.org/HOWTO/Partition/formatting.html)
> When a hard drive is partitioned, it is mapped into sections, but the sections are empty. It is like a newly constructed library; shelves, signs, and a card catalogue system must be put in place before the books are put away. Note that formatting a partition will erase all and any data in that partition. I don't know what options that "format" button gives you, but you can use ext3 if it's gonna be accessed by linux only, or fat32 if you will access it in both windows and linux.

---

