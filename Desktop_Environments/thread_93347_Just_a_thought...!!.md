---
title: "Just a thought...!!"
date: 2005-11-21
forum: Desktop Environments
---

### Post by tomwell on 2005-11-21
Hi just a thought,

how dangerous is it to have my fat32 partition booted on startup and my ntfs partition aswell???

I am wondering because i have been told its not recomended...

Thanks for any info!!

Peace 

Tom

---

### Post by jdong on 2005-11-21
Can you clarify what you mean?

---

### Post by 23meg on 2005-11-21
If you mean mounting these on startup by adding them to your fstab, it's not dangerous; you've been misinformed.

---

### Post by tomwell on 2005-11-21
Ok i was just told that perhaps it would facilitate a virus executing itself on my machine... since a windows read write partition is accessible to anyone that could potentioaly takes over my pc...

Just a thought...

Peace 

Tom

---

### Post by jdong on 2005-11-21
No, it's indeed perfectly safe to do so (doesn't facilitate viruses in any way I can dream of, and I consider myself pretty security conscious)

Only thing is that more FSes may be affected by the potential for corruption in case of a bad shutdown... NTFS and most Linux FSes are pretty resilient to such kinds of damage, but FAT32 may not be as thrilled!

---

### Post by tomwell on 2005-11-21
Jdong,

Thanks for your quick response...

I am now reassured so i can use the easyness of having a boot up mounting of my partitions...

What are Fses i am a noob so i have no ideas...

Thank you for your insight and judging from your number of posts i assume you are either a very chatty person or a linux geek....!!! LMAO!!!!

Once again thank you!

Peace

Tom

---

### Post by towsonu2003 on 2005-11-21
[QUOTE=tomwell]
What are Fses i am a noob so i have no ideas...
[/QUOTE]

filesystems

like fat32, ntfs, ext3, ext2, etc.

---

### Post by jdong on 2005-11-21
Sorry for the quick shorthand, but yes, Filesystems... You'll find much better articles about filesystems on Wikipedia ([http://en.wikipedia.org/wiki/Filesystem](http://en.wikipedia.org/wiki/Filesystem), also see Journaled File Systems), if you're ever curious... Typically it's a transparent aspect of the Operating System that you'll never have to worry about :) Just know that it stores all your data, and that Linux provides the choice of several different filesystems that all have their advantages/disadvantages unique to them.

---

### Post by tomwell on 2005-11-21
Thanks Towsonu2003,

Hiow goofy of my not to realise fses are filesystems... LMAO!!!!

Jdong hope you not offended by my goofy comment...!!!

Peace to all

Tom

---

### Post by tomwell on 2005-11-21
we must of anwsered at same time... LOL

I am super interested in everything Ubuntu... Its 3.30 am on a monday nigth and am still awake browsing the forums... lmao am intrerested...!!! LMAO

Will lokk into fses...

Peace

Tom

---

### Post by jdong on 2005-11-21
LOL, we're just tripping all over each other :)

Yeah, response time around here is pretty fast. More than one person eager to answer questions.

---

### Post by tomwell on 2005-11-21
Talking about tripping am about to trip all the way to bed... am exhausted...!!!

At least am reassured that mounting my fat32 partition is safe...!!!

Good night to all!

Peace

Tom

---

