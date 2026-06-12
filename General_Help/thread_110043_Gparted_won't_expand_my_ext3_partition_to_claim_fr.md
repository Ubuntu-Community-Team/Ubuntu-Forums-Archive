---
title: "Gparted won't expand my ext3 partition to claim free space"
date: 2005-12-29
forum: General Help
---

### Post by frostoftheblack on 2005-12-29
Hello, I originally installed WinXP on this laptop but then took out 10GB for linux, not thinking that it would become my main OS. Now I want more space for my ext3 partition and less for my ntfs partition. I tried loading the liveCD, then running gparted. It lets me shrink my ntfs partition to the minimum (where the data stops I think) but then it won't let me increase my ext3 partition to reclaim that free space.
I was thinking it was because the free space was in _front_ of my partition but I think I should be able to still expand it, right?

There is a screenshot of it here :
[http://paste.ubuntu-nl.org/6355](http://paste.ubuntu-nl.org/6355)



(By the way, wasn't sure if this is an appropriate forum for this topic, couldn't think of a better one).

---

### Post by Zelut on 2005-12-29
As far as I understand the problem here is Microsoft not playing well with others.  Unfortunately we can't resize/edit an NTFS partition.  If it had been in a FAT format we'd be ok..

Sounds like you'll need to backup what you have and do a fresh install using 100% of your drive if thats what you need.

---

### Post by stuporglue on 2005-12-30
> As far as I understand the problem here is Microsoft not playing well with others. Unfortunately we can't resize/edit an NTFS partition. If it had been in a FAT format we'd be ok..

Incorrect!

Resizing an NTFS partition IS possible, and with great success. The Ubuntu installer for x86 (and ADM64?) does it automatically if you say to resize. 

The original poster also said the NTFS was already resized. It's the ext3 partition that won't resize. 


Parent Poster: 
Did you actually write changes after this resize? If so, can you boot to the CD  and try the partitioner again? If it doesn't work....

Boot into Windows and let it defrag, check the disk size to make sure it actually *did* get resized. 

Try using a Knoppix CD if that is an option. It includes qtparted, which I prefer over Gparted. Minimal under the hood differences (if any), but maybe it makes a difference? 

Good luck

---

### Post by frostoftheblack on 2005-12-30
[QUOTE=stuporglue]
Did you actually write changes after this resize? If so, can you boot to the CD  and try the partitioner again? If it doesn't work....
Boot into Windows and let it defrag, check the disk size to make sure it actually *did* get resized. 
Good luck[/QUOTE]

Actually, I didn't.
I was considering it too but I didn't want to do it if I wasn't going to be able to grow my linux partition immediately afterwards. I'll let you know what happens after I write changes for that part.

---

### Post by plors on 2005-12-30
well, it's not possible to move the start of an ext3 filesystem. 
What you should do is:

- copy /dev/hda2 to the free space before it (using gparted's copy functionality). 
- if (and only THEN!) that's succesfull, delete the old /dev/hda2
- then grow the copy (most likely named /dev/hda4) to fill the free space.
- update your /etc/fstab if needed.

that's all :)

---

### Post by plors on 2005-12-30
[QUOTE=stuporglue]Incorrect!

<snip>

Try using a Knoppix CD if that is an option. It includes qtparted, which I prefer over Gparted. Minimal under the hood differences (if any), but maybe it makes a difference? 

Good luck[/QUOTE]
Hi,

1. Why do you prefer qtparted?
2. there are HUGE under the hood differences. the only thing they have in common is the fact they use libparted to handle raw partitions. Dealing with filesystems is implemented quite different.

cheers..

---

### Post by stuporglue on 2005-12-31
> 1. Why do you prefer qtparted?

Probably because it hasn't failed me yet :-) Gparted is probably just as good, but I haven't used it enough to have confidence in it. My idea was more maybe-something-different-would-work than qtparted-is-better. If the begining of an ext3 can't be moved though, I guess it doesn't matter what he uses.

---

