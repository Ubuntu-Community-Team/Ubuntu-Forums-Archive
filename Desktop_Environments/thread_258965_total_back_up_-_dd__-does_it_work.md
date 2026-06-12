---
title: "total back up - dd  -does it work?"
date: 2006-09-16
forum: Desktop Environments
---

### Post by recklessray on 2006-09-16
hello.

any linux savy ppl, please advise me on this question...

i have a lovely ubuntu system purring like an over fed kitten lying next to a particulaly warm fire on a sheep skin rug with... well, you get the idea. im fairly paraniod about my hard drive dying, not that there are any signs of it - but i work in service support and i know how unreliable ide drives are.

right. i have two western digital, 80 gb drives (and others) in my ubuntu box. ubuntu is on hdb and the other western digital 80 gb drive is hdg. ive just run the following : dd if=/dev/hdb of=/dev/hdg 

its copying as i type. my question is this - will it 'just work' if hdb goes down one day and i put hdg in its place? i could just back up /home / /etc but then id have to install everything else and this is my every day, family pc that i also use for work and host my website - ftp etc so i really want to keep downtime to a minimum... an i doing the best thing, can anyone offer any alternatives, has anyone done this and what happened???

any help is most gratefuly received!

ray :)

---

### Post by recklessray on 2006-09-16
anyone?

---

### Post by lamego on 2006-09-16
dd would work but you could use partimage which is more ghost alike, much more friendly to use.

---

### Post by thoughts on 2006-09-16
I'd say that rsync is a much better tool for this than dd.  It can do incremental backups, i.e. only copy the files that have changed since your last backup, so after the first time it will be much quicker than dd'ing the whole thing again.  Just do:

mount /dev/hdg1 /mnt/backup
rsync -av --delete --exclude /mnt/backup / /mnt/backup

(Assuming hdg1 is your main system+data partition.)

This will make /mnt/backup an exact copy of / (except that it will exclude /mnt/backup, of course).  The -a option basically means "mirror everything including ownership info, permissions, etc."  The -v option means verbose, i.e. show the files as it copies them.  The --delete option means "if some file on the backup no longer exists in the source, then delete it from the backup too" (i.e. some file that you intentionally deleted/moved/renamed on the source).

Of course if you want to be able to just move this disk over and make it your primary disk should your main one die, then you'll need to manually create the same partition structure on the backup disk beforehand.  Maybe the best thing would be to use dd for the first time, which will create the partitions as it goes (right?), and then use rsync after that for your weekly backups.

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by recklessray on 2006-09-17
very many thanks  - ive heard of rsync - ill have a look at it today. 

 - best regards, ray :)

---

### Post by lamego on 2006-09-17
Does rsync properly handles device files ? Woud the rsync copy allow for a full system recovery ?
I do use rsync for /home backups, but I am not sure about system backups.

---

### Post by dwasifar on 2006-09-17
Does dd copy the boot sector and everything when used in this way?  Will it result in a bootable disk?

---

### Post by thoughts on 2006-09-17
Yes, rsync does copy device files.  Run "man rsync" and you'll see this on about the second page:

- support for copying links, devices, owners, groups, and permissions

The rsync backup would allow for full system recovery in terms of data: all the files would be there (your personal files as well as all system files).  But it doesn't handle things like making sure your partition structure is set up properly, making sure the boot sector is correct, etc.

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by daxelrod on 2006-09-17
While other tools are available and might be more appropriate for routine backups, dd does in fact work. Quite well.

I recently had to deal with a disk with several partitions. The parition table itself was messed up, and one of the partitions contained an NTFS filesystem that for other reasons became corrupted. The disk hardware was fine, though.

I tried a number of complex backup tools. What finally worked was to just use dd to make a copy of each partition onto another drive (once I figured out where the partitions started and ended). Each backup is now mountable as a loopback device if neccessary, and everything was preserved in the exact state it was in. I should clarify that I told dd to use a regular file in the "of" paramter rather than another device.

I tried using several other tools, all of which ran into problems. dd was the simplest and it was the one that worked.

---

