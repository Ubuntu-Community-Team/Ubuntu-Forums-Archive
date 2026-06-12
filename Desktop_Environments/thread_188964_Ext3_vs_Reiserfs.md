---
title: "Ext3 vs Reiserfs"
date: 2006-06-04
forum: Desktop Environments
---

### Post by eddorey2k3 on 2006-06-04
Howdy!

So yeah. I've got my 6.06 up and running as I want it, and now comes the time to start getting more and more stuff onto it. I will soon be adding another hard drive (I've got a spare 40gb drive kicking about, and this already has a 160gb in it, plus my 250gb backup drive :P).

Anyway. I need to obviously format the spare drive, and then I can add it in. I was wondering what peoples views/opinions were on which file system would work better under Dapper? I noticed from the installer that it no longer even asks how you wish it to install the default system, just goes to Ext3. Am I right in thinking this is a deliberate move, since Ext3 has better support, or just how things have turned out?

It's looking like Ext3 will be easier, but it'll be interesting to see what people say.

Oh, it'll mainly be used for MP3's and the odd movie.

---

### Post by JoWilly on 2006-06-04
Reiserfs is faster (especially if you have many small files). Ext3 is slower, but is said to be more "crash proof".

I personnaly have reiser on my root and work partitions, and ext3 on my 2 backup partitions (where I keep my important docs, etc...).

---

### Post by tribaal on 2006-06-04
Well ext3 is the most common linux filesystem. It's robust and behaves well under most circumstances. ReiserFS's major difference is that a single file can be much bigger (ext3's maximum filesys is 2Tb, ReiserFS is 8TiB).

Overall, I'd say ReiserFS is only to be used in very few cases (fileservers serving Tb-size files), other that that and personal preference, ext3 is perfectly suitable.

Cheers 

- trib'

---

### Post by az on 2006-06-04
Any performance advantages reiserfs has (I.E. in a situation with directories with millions of small files) is wasted on a desktop.  You will not see any performance difference with either filesystem on a desktop system.  

There is no reason to use anything else that ext3.

---

### Post by JoWilly on 2006-06-04
[QUOTE=azz]Any performance advantages reiserfs has (I.E. in a situation with directories with millions of small files) is wasted on a desktop.  You will not see any performance difference with either filesystem on a desktop system.  

There is no reason to use anything else that ext3.[/QUOTE]

Sorry, I use reiser on my root partition in raid 0. It is faster (beagle indexing, scaning of photo libraries, rythmbox indexing mp3s, etc...).

Furthermore, reiserfs gives me more space on my disks. I have tried formating ext3 with removing the 5% it allocates for root (lost space), but even with this my ext3 partions are smaller than if they are formatted with reiser. And of course, by default ubuntu does not offer any way to recover this lost space... so it is what it is ... lost space -> how much is 5% of a 160 Gb partition ?

I lose several GB with ext3, this is a lot. And most people don't even know it.

So especially with beagle indexing, reiser is faster for me.

---

