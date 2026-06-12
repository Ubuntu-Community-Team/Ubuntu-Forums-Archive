---
title: "parted limitations?"
date: 2006-02-04
forum: Desktop Environments
---

### Post by kabanta on 2006-02-04
I have a partition that I would like to make larger. Unfortunately, there is an ext3 partitition between it and the free space:

[partition to increase][ext3 partition][free space]

It seems that parted (and presumably gparted and derivatives) require that the start of an existing  ext3 partition remain fixed. Is this correct? (So far, I have been able to increase the size of the ext3 partition, but not "move" it. But perhaps there is a parted or gparted trick I do not know.) If this really is a limitation of parted/gparted, is there some other tool that will allow me to move the starting point of the ext3 partition (so I can then increase the size of the first partition)? I would really prefer not to have to reformat and re-install everything.

Any tips much appreciated.

---

### Post by Parkotron on 2006-02-04
I had a similar, but somewhat different, issue not too long ago. I was able to "move" a ext3 partition by copying it to the desired location and deleting the original. There are, however, some major restrictions to this method: it requires a lot of free diskspace and if you're not careful the partition number could change, rendering the ext3 partition unbootable.

---

### Post by Herman on 2006-02-04
I like to play around with partitions a lot (just for fun), and one way of doing things if you have enough disk space is to play 'partition leapfrog'. 
Normally you need to shrink your partitions first (copy all files to CD or DVD or some other media and then delete them). This also serves the double purpose of making sure they are all backed up properly. Make two copies of them to be sure.
Then copy the Linux (ext3 or reiserfs) partition somewhere out of the way. (Like up to the end of your disk). It will be given a new partition number, that's okay for now. Delete your original Linux partition.
Now that that's out of the way, resize your NTFS or FAT32 or whatever.
When you copy your Linux partition back again it will receive the same partion number it had before. 
If you need to delete the swap area, make the new partitions in the reverse order of when you deleted them, and place your swap back on the same side of your Linux partition as it was before. I'm not sure if that's critical or not, but it seems to bring me good luck. 
If you do end up with different partion numbers, you can edit /etc/fstab.

Tip: you don't have to delete your spare copy of your Linux partition at the end of the disk if you can afford the 3.0 GB or so investment in disk space. You can leave it there for a back-up. It has no files in it, but has all your tweaks and customizations, added software, and that sort of thing. 
Well that's what works for me, I hope it helps you too, good luck with it! :-D (Herman)

---

### Post by kabanta on 2006-02-04
Thanks to you both for the tips. I think I've got it, but just want to double-check I understand about the "copying."

First, I assume you mean I should use the actual "copy" command (rather than "move" which seems to have the limitations I indicated earlier). 

Also, this comment confuses me:
[QUOTE=Herman]Tip: you don't have to delete your spare copy of your Linux partition at the end of the disk if you can afford the 3.0 GB or so investment in disk space. You can leave it there for a back-up. _It has no files in it_, but has all your tweaks and customizations, added software, and that sort of thing.[/QUOTE]
If I am copying it back and forth, how is it that the one at the end of the disk will "have no files in it"?? At the end of this process, won't I wind up with two partitions with the same content? (Which is fine.)

---

### Post by Herman on 2006-02-04
> If I am copying it back and forth, how is it that the one at the end of the disk will "have no files in it"?? At the end of this process, won't I wind up with two partitions with the same content? (Which is fine.) Yes, as long as you have enough disk space, it's quite okay to leave all the files in there if you want. I did suggest deleting them all, in case you need to shrink your partition first to make room to manouvre it. You don't have to if you don't need to. It's just a more conservative way of doing things. Lots of people these days such nice big hard disks so they don't need to worry so much about things like that. 
Doing that would serve the double purpose making sure they are all definitely backed up, and allowing you the option of leaving the minimal sized temporary partition you make at the end of the disk as a back-up of your install. If you can afford the extra space it's okay to leave the files in that as well. Or just delete it if you don't like that idea.
 Please make sure your files are backed up on some other media also. (Of course). :-D (Herman)

---

### Post by kabanta on 2006-02-04
[QUOTE=Herman]I did suggest deleting them all, in case you need to shrink your partition first to make room to manouvre it.[/QUOTE]
Ah, ok, I didn't understand that from the earlier description. So, the initial proposal was: 
a) make backups (!), 
b) delete the contents of partition to be moved, 
c) reduce it, 
d) copy the reduced version (which will nonetheless have preferences, etc.) to temp location (end of disk), 
e) delete the original reduced version
f) expand the first partition into the newly-available space
g) copy the tmp partition from end, back so it is next to first partition
h) increase the "restored" (shrunken) ext3 partition to original size
i) copy back in files from backup to full-size ext3 partition

I don't have *very* much extra space to maneuver, so I may need to do it this way.  I'll try this tomorrow when I'm a bit more awake -- and post update. Thanks.

---

### Post by Herman on 2006-02-04
> First, I assume you mean I should use the actual "copy" command (rather than "move" which seems to have the limitations I indicated earlier).  Yes, the first time I tried something like this I was using the Ubuntu install CD partitioner, but I was [resizing my Ubuntu partition.]("http://www.ubuntuforums.org/showthread.php?t=105255")
I have also tried out the 'copy' command in the 'parted' (CLI), but lately I have become lazy and prefer the new GParted livecd-0.2 for doing this type of operation. (My second sig link leads to the .iso download site for that).
I think it's really the same software underneath that does the work (parted), so I am most likely just using three different ways of accessing the same command. :-D (Herman).

---

### Post by Herman on 2006-02-04
> a) make backups (!), 
b) delete the contents of partition to be moved, 
c) reduce it, 
d) copy the reduced version (which will nonetheless have preferences, etc.) to temp location (end of disk), 
e) delete the original reduced version
f) expand the first partition into the newly-available space
g) copy the tmp partition from end, back so it is next to first partition
h) increase the "restored" (shrunken) ext3 partition to original size
i) copy back in files from backup to full-size ext3 partition
That looks correct to me.  And if your swap area was already at the end of the disk, and not in the way, you can just leave it alone, of course. 
But if your swap area is in the way and you need to delete it, before you finish just make a new swap in the same position relative to your Ubuntu partition as it used to be. (I'm might only be acting superstitious here, I'm not sure how important this part is. I test these ideas out on an older computer, and sometimes it's the old computer hardware that causes incidental problems, not related to my experiments.  I do remember having OS troubles after placing the swap on the wrong side. I don't recall if it had a different partition number or if I knew about editing /etc/fstab back then. Maybe that's all that was wrong.)
Good luck with it! :-D (Herman)

---

### Post by kabanta on 2006-02-05
Well, it is all now working the way I want, but it turns out that I had to do a number of more complicated moves. (My system is on a work-laptop with certain software I cannot remove. It seems to interact with partition operations.) The copying back and forth is a good trick to remember.

[QUOTE=Herman]I have become lazy and prefer the new GParted livecd-0.2 for doing this type of operation[/QUOTE]
Yes, I tried the gparted 0.2 livecd recently, but it stalls on my hardware :-(

Thanks again for the suggestions.

---

### Post by plors on 2006-02-05
[QUOTE=kabanta]
Yes, I tried the gparted 0.2 livecd recently, but it stalls on my hardware :-(
[/QUOTE]

Did you file a [bug]("http://gparted.sourceforge.net/bugs.php") ?

---

