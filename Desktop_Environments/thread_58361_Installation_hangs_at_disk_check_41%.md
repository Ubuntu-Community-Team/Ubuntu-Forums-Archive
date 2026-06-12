---
title: "Installation hangs at disk check 41%"
date: 2005-08-19
forum: Desktop Environments
---

### Post by ironfistchamp on 2005-08-19
Hey I'm new to this whole linux game. I have had a few abd experiences with Suse and Libranet but thought I would give it another try. 

Anyway on to the problem.  I downloaded and burnt kubuntu and the installation gets to the bit where it checks the hard disks but freezes at 41%

I have two sata disks and one has XP home...the other is unformatted.

Any help resolving the issue would be great.

Thanks

Ironfistchamp

P.S Nice Smilies you've got here  :smile:

---

### Post by Takis on 2005-08-21
You may like to download the iso image again, and verify that its md5 sum is consistent with what's posted on the downloads page.

---

### Post by JLTB on 2005-08-22
Hi,

I had a similar problem once with a hard-disk that was slowly going sour on me.  You might want to check your disks in either windows or linux.  Do a full scan if unsure, the quick ones can miss stuff.

---

### Post by skoal on 2005-08-22
I actually had a similiar problem like that one two different occassion, on two different installs.  The solution for _me_ was to add/modify my partition table entries.  Redo the install and create a minimum partition table entry like (for example):

/boot - 64-128 MB (reiserfs or whatever)
swap - whatever amount
/ - the rest of the disk (reiserfs or whatever)

When I did that, by accident or mere coincidence, it never hung at any part of the install again.  

However, in your case it may be SATA related.  There are several such SATA related threads in these forums pertaining to your case (and others).  That may be the problem as well.  I'd change your partition info first and see if the install completes.

\\//_

---

