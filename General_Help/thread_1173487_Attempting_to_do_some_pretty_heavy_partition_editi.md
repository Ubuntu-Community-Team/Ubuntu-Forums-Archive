---
title: "Attempting to do some pretty heavy partition editing, need help"
date: 2009-05-29
forum: General Help
---

### Post by Vunutus on 2009-05-29
Here's a screenshot of how my disk is set up now:

[[IMG]http://img211.imageshack.us/img211/2312/screenshotdevsdagparted.png[/IMG]](http://img211.imageshack.us/my.php?image=screenshotdevsdagparted.png)

Now it might be obvious by looking at it but here is what each drive is:

sda1: Windows XP
sda2: Media (mostly music)
sda3: swap
sda4: Ubuntu

My Ubuntu partition is becoming rather crowded, so I'd like to swap around some partitions (without reinstalling everything) to make some space. What I mainly want to do is get rid of the media partition and merge that space in with my Ubuntu partition. In addition, I'd like to skim some space off my XP partition and add it to Ubuntu since I rarely use Windows anymore. I'm thinking about taking 50GB or so away from XP.

How do I go about doing this? Obviously I'll need to free up some space on my Windows partition and defragment it before doing anything, but other than that do I just start chopping away in GParted?

Also, is it possible to edit a currently mounted partition or do I need to do this from a live CD?

---

### Post by merlinus on 2009-05-29
You cannot change a mounted partition, so use gparted live cd.  Also, your media partition is formatted as ntfs, so linux cannot use it.  Back up important data, and format it as ext3 (or ext4).

I would also move your swap partition to the end of the disk, so future resizing will be easier.

---

### Post by Sef on 2009-05-29
I would shrink both XP and Ubuntu.   Make the home partition bigger.   That way too your data will be safer if one of your oses crashes.   XP, I would make 20 gb and Ubuntu 10 gb.  Except for swap, the rest I would use for a home partition.

---

### Post by lisati on 2009-05-29
> **merlinus said:**
>  Also, your media partition is formatted as ntfs, so linux cannot use it. 

Support for NTFS is better these days: the copy of 9.04 on my other laptop, which shares the HDD with Vista, can access the NTFS partition no trouble without the need for messing about installing tools like ntfs3g

---

### Post by AndyCooll on 2009-05-29
As already mentioned you can resize to your hearts content, however you'll need to do it using the Live CD.

If you do resize your partitions, as Sef indicated it might be a good idea to create a new partition and put your /home folders on it.

The easiest time to do that is when doing a fresh install, although it is possible to "move" your current home partition.

Anyway, once your /home is on a partition of it's own the idea is that if you needed to do a reinstall your settings and such like are preserved.

:cool:

---

### Post by Vunutus on 2009-05-29
Is the GParted live cd interface fairly self explanatory or will I need to get some guide? 

How complicated is it to move the /home directory to another partition? Will GParted automatically update configuration files in Ubuntu to point at it (FStab I think?) or do I need to do that myself?

---

