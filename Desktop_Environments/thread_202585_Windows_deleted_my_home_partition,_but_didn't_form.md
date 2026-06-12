---
title: "Windows deleted my /home partition, but didn't format it!  Help"
date: 2006-06-23
forum: Desktop Environments
---

### Post by naked on 2006-06-23
Is there anyway to get it back?  I was installing the new Vista beta to give it a look, and I selected an old partition for it to delete and then to format, but it ended up taking that partition, and my home partition out!

Can I somehow recreate my parition table?

HELP!

L

---

### Post by dglock on 2006-06-23
[QUOTE=naked]Is there anyway to get it back?  I was installing the new Vista beta to give it a look, and I selected an old partition for it to delete and then to format, but it ended up taking that partition, and my home partition out!

Can I somehow recreate my parition table?

HELP!

L[/QUOTE]


   You are in the wrong forum! This is a linux forum.

   You need to post in the microsoft forums!

don

---

### Post by naked on 2006-06-23
Perhaps my question was not specific enough.  I've been running Ubuntu since Warty, and I usually have 2-3 paritions that I can play around with.  I wanted to use one of them to install Vista to check it out on.  But when I went to delete it, it also delete my linux /home partition.  It didn't format anything, just deleted them from the parition table.  Is there a way via Ubuntu (or anything else) to restore my partition table?  It nuked my home directory partition and my swap file partition and put them in to one unallocated section.  I know that my home partition was first, but I don't remember the exact size, it was around 9.3/9.5 GB, and my swap was around 1.5GB.  

Anything I can try?

L

---

### Post by TechHut on 2006-06-23
[QUOTE=dglock]You are in the wrong forum! This is a linux forum.

   You need to post in the microsoft forums!

don[/QUOTE]
I disagree. We should be giving answers, not a referral to another forum. Also, FYI, there is no official Microsoft forum, only ran by the users.

Now naked, I don't know the answer, but one place I would really try is the ubuntu irc.

---

### Post by linuchsan on 2006-06-23
Try testdisk

---

### Post by naked on 2006-06-23
Well first scan by testdisk found everything but my lost home partition.  I'm doing a deeper scan, and then I am going to try 'gpart' to see if it works.

Any other ideas/suggestions?

L

---

### Post by naked on 2006-06-23
Still no luck, it looks like it might have found something, but I am not sure by looking at this.

Anyone more familiar?

I've attached an image.

L

---

### Post by chaosblue on 2006-07-15
Since you have a copy of Windows, I'd recommend getting Kernel Linux ([http://www.nucleustechnologies.com/)](http://www.nucleustechnologies.com/)).  I've used it several times now to recover data due to bad partitions, accidental deletions, and a corrupted hard drive.  I felt it was very much worth the money (which isn't much... about $45 IIRC).

---

