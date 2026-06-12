---
title: "Changing from NTFS to Ext3"
date: 2009-06-15
forum: General Help
---

### Post by Gp. on 2009-06-15
Okay well I'm previously a windows user, and two of my storage hard drives are NTFS. One is 1TB the other about 400GB.

They are very full.

It's probably stupid to ask, can you convert ntfs to ext3?
Otherwise how am I going to do this? Cause I can't format them with the data on there, and I have no way to back up these 2 drives.

I would have to buy another drive, maybe 2TB, back the data up, then format the drives and put it back.

I don't wanna use NTFS when I'm running Ubuntu...

---

### Post by mixmaster on 2009-06-15
You have nearly 1.5Tb of unbacked-up data running on a filesystem alien to the OS you are using?  I would have thought that buying a backup drive would have been one of the first things you would do,

I am unaware of any in-place utility for converting NTFS to EXT3, but even if such a beast existed I would be very reluctant to run it without backing the data up first.

---

### Post by Jive Turkey on 2009-06-15
AFAIK there is no safe way to do what you are asking.  What is your motivation for not wanting to use ntfs with ubuntu?  The ntfs driver that ships with ubuntu works pretty well, it shouldn't have any problems reading and writhing to the drives.

If you are up for an unsafe method you could tediously make as much free space on the 1TB drive as possible, make a new partition with the type you want, move as much data from the old one to the new partition as possible then shring the old and grow the new over and over.  I dont reccomend this at all and I think you would more likely lose all of your data trying it.

1.5 TB drives aren't that expensive and it sounds like you are running low on storage anyway.

---

### Post by Gen2ly on 2009-06-15
I've never heard of a ntfs to ext3 conversion program, so probably no.  You'll have to find a way to transfer those files to another drive/partition and then format it if you really want ext3.  That said I'm not sure that's really necessary, NTFS support is pretty good and I've never had a problem with it.

---

### Post by Gp. on 2009-06-15
Well considering ext3 maintains itself and defrags on its own and such (so ive been told) it sounds like the better one to run with.

---

### Post by RD1 on 2009-06-15
> Okay well I'm previously a windows user, and two of my storage hard drives are NTFS. One is 1TB the other about 400GB.

They are very full.

It's probably stupid to ask, can you convert ntfs to ext3?
Otherwise how am I going to do this? Cause I can't format them with the data on there, and I have no way to back up these 2 drives.

I would have to buy another drive, maybe 2TB, back the data up, then format the drives and put it back.

I don't wanna use NTFS when I'm running Ubuntu...

Let me answer your question with another. What are you going to do when these drives fail and you lose nearly 1.5TB of data? 

Seriously, break down and buy a new drive. Format it in ext3, backup all the data from your old drives, reformat the old drives to ext3 and copy back your data. Viola! Your NTFS drives are now ext3 AND your data is safe.

Please! Before your next post is "How do I recover data from a failed NTFS drive?

---

### Post by t0p on 2009-06-15
> **Gp. said:**
> Well considering ext3 maintains itself and defrags on its own and such (so ive been told) it sounds like the better one to run with.

You want to convert your drives to ext3 because you "heard" it's better?  Cool.

Anyway, you can't.  Backup your data, then reformat the drives.

Or you could just stick with NTFS.  Ubuntu can read and write to NTFS just fine.

Either way, you should backup your data. Now.  One day your 1 TB disk is gonna take a dump, and you'll be gutted if you haven't backed it up.

---

### Post by Gp. on 2009-06-15
Touche'
Looks like I need money for upgrades :(

---

