---
title: "Just want to increase the size of my partition"
date: 2009-05-31
forum: General Help
---

### Post by kmaster228 on 2009-05-31
hello all i recently instaled ubuntu on a 15 gb partiton dual botting with vista... i have realised that i5 gb isnt enough for my needs... i simply want to increase my partition size without losing any data or making a new partion.. i have gparted installed. i have included a snap shot of what gparted looks like in my case [ATTACH]115856[/ATTACH]

---

### Post by CatKiller on 2009-05-31
You can't modify a partition that's mounted. You'll need to run GParted from the live cd.

Shrink the partitions that you want smaller, move the partitions that you want bigger to the left into the unallocated space, and then expand them. Your Ubuntu partitions are in an extended partition, so you'll need to make that bigger before you can make them bigger.

---

### Post by dandnsmith on 2009-05-31
Are you prepared to blitz the existing installation of linux, and start over - seems to me this is the easiest way:
-get rid of the extended partition and its contained logical partitions
-resize the second NTFS partition (I'd back it up first)
-allocate the space for the new extended partition, and create the linux and swap partition
-redo the installation

There are a few variants possible - these are only my initial reaction

---

### Post by kmaster228 on 2009-05-31
@dandnsmith this seem hard to do and i dont want to delete my ubuntu partion as i have alot of files and programs which will take forever to reinstall
and @ catkiller do i need to backup my windows partitions and will i lose any data?

---

### Post by CatKiller on 2009-05-31
> **kmaster228 said:**
> do i need to backup my windows partitions and will i lose any data?

You **always** need to back up your data. Even when you aren't messing around with the partition tables.

These are non-destructive operations, and if you've backed up your data then it's bound to go perfectly smoothly. The time that it doesn't will be the time that you haven't made a backup. There's always human error, or power cuts, or any number of things that could mess things up.

---

### Post by kmaster228 on 2009-05-31
im sorry if i seem like a noob but how do you back up on ubuntu?

---

### Post by Legace on 2009-05-31
> **kmaster228 said:**
> im sorry if i seem like a noob but how do you back up on ubuntu?

You don't need to backup Ubuntu, because you can always reinstall it. Just backup any files (Word documents, PDF files, music, videos, etc.) that might be of importance to you. You should copy them over to a USB disk/external harddrive (reccomended),  DVD, or another partition [that you are NOT going to edit] (least reccomened).

---

### Post by kruegger on 2009-05-31
I'd be looking for a second HDD if I were you. Why?
You store a lot of stuff and have three O.S.'s installed. 
Backing up is going to be one of your main issues sooner than later.
And you're desesperately running out of space, which reduces system stability to partition handling

I would not do anything until you are able to back up your stuff, whatever it takes.

Partimage could do for you,but you need practice in backing up and restoring. You can start for unimportant little files. 

Before reducing the size of a ntfs partition, I'd run defrag or the Vista equivalent first, to compact the file system.

If, in spite of all above said, you want to play hard, [look here]("http://www.subirimagenes.com/imagen-pantallazo-2642432.html")

---

### Post by kmaster228 on 2009-05-31
ok so i copied all my important stuff from ubuntu, not from windows cuz i have way too much stuff on that... then i defrag windowa pop in the live cd open gparted and just drag my windows partion 15 gb shorter then drag the ubuntu partion filling in that unallocated space

---

### Post by CatKiller on 2009-05-31
That sounds about right. Don't forget your other partitions are inside an extended partition (coloured cyan) so you need to make that one bigger first.

---

