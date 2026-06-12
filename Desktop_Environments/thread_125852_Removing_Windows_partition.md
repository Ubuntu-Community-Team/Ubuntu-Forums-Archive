---
title: "Removing Windows partition"
date: 2006-02-05
forum: Desktop Environments
---

### Post by Psimon on 2006-02-05
I removed my Windows partition using GParted, but I couldn't resize my home partition to take advantage of the freed space - it said "device busy". Now I have that old hda1 partion listed as "Unallocated".

Can anyone tell me how to add this unallocated space to my home partition?

---

### Post by gerbman on 2006-02-05
[QUOTE=Psimon]I removed my Windows partition using GParted, but I couldn't resize my home partition to take advantage of the freed space - it said "device busy". Now I have that old hda1 partion listed as "Unallocated".

Can anyone tell me how to add this unallocated space to my home partition?[/QUOTE]

I believe you can just boot an Ubuntu Live CD and use GParted from there.  Remember the device name for your home partition, and when you get into GParted in Live just resize that same partition.  Should do the trick.

Cheers!

---

### Post by Psimon on 2006-02-05
Thanks for your advice.

I couldn't find gparted on my live CD - it is a Hoary live CD? Do I need the breezy version?

---

### Post by gerbman on 2006-02-05
[QUOTE=Psimon]Thanks for your advice.

I couldn't find gparted on my live CD - it is a Hoary live CD? Do I need the breezy version?[/QUOTE]

Yeah, I would give that a try.  It showed up for me in Breezy Live.

---

### Post by Psimon on 2006-02-05
I was able to access the disk through GParted on the Breezy live CD, but I couldn't resize the partition. The free space is at the front (if that's the right word), but there was no option to increase the size of the ext3 partition in that direction - it said there was no free space before it.

Any more ideas?

---

### Post by plors on 2006-02-05
You cannot move the start of a ext3 filesystem. You could however try to copy the ext3 filesystem to the unallocated space, remove the original partition and resize the copy to fill up the just freed space.

This is a proven method and won't endanger your data. The only thing you need to keep an eye on is the fact the partitionnumber will most likely change, so you have to update your /etc/fstab.

You can do al this using gparted (i recommend using the latest [livecd]("http://gparted.sourceforge.net/livecd.php"))

cheers

---

### Post by Psimon on 2006-02-05
[QUOTE=plors]You cannot move the start of a ext3 filesystem. You could however try to copy the ext3 filesystem to the unallocated space, remove the original partition and resize the copy to fill up the just freed space.

This is a proven method and won't endanger your data. The only thing you need to keep an eye on is the fact the partitionnumber will most likely change, so you have to update your /etc/fstab.

You can do al this using gparted (i recommend using the latest [livecd]("http://gparted.sourceforge.net/livecd.php"))

cheers[/QUOTE]


Thank you very much - I'll give it a try (probably next weekend).

In the meantime can you tell me how to update /etc/fstab? that's uncharted territory for me.

---

### Post by Peter41az on 2006-02-06
i think in order to copy to that partition, it has to be the same size or larger than the partition you are copying from. (in response to moving the ext3 filesystem) hope its working out for you.:p

---

### Post by plors on 2006-02-06
well.. you don't copy to a partition, you copy to free space! A fitting partition will be created.

You are right when saying that free space needs to be able to hold te partition :). Sometimes it's necessary to shrink the sourcepartition before copying it.

---

### Post by gerbman on 2006-02-06
[QUOTE=Psimon]In the meantime can you tell me how to update /etc/fstab? that's uncharted territory for me.[/QUOTE]

First, read up on /etc/fstab [here]("http://www.linuxchix.org/content/courses/filesystem/Lesson5.html"). It's pretty straight-forward. Now, suppose your new free space partition is /dev/hda1 and your current home partition is /dev/hda4 with a few partition in between. You can create the new partition in the free space and copy your home directory over. Then you need to modify your fstab to account for the changed home partition. You'll just need to change the mounted device for the line mounting to /home. Next you could just reboot and the system will mount the new home partition at /home and will leave the old home partition unsed. Next just delete the old home partition (assuming the new one checks out okay), then you should be able to play around with the starting and ending points of the other partitions to shift them all to the right, resulting in the new home partition gaining the extra free space. 

Obligatory disclaimer:  I haven't tried this procedure, but it should be okay. I think even GParted refers to itself as a "potential weapon of mass destruction", meaning it is _very_ important to have a clear idea of what you are doing and to back up your data before you start whacking partitions and moving them around. Of course, the worst that could happen is that you have to reinstall the system, which is fine if you backed up your important data :-)

Cheers, and good luck!

EDIT:  After all that, I failed to notice Psimon's point that you can't change the start of an ext3 partition in GParted, which you have to be able to do in order to shift the free space around. lol (below) seems to think there are tools out there to do this.

---

### Post by lol on 2006-02-06
> You cannot move the start of a ext3 filesystem.

Really? Then this is a missing feature in gparted... I used to modify my partition table without any problem using Windows tools (like partition magic for example). I never had any trouble to move an ext3 partition.

I no longer have Windows installed, and I must say that I am a little bit worried that next time I will have to modify my partition table, I will have to use a Linux tool. The only time I tried to one (it was qparted) I made a mistake and lost all my data :(

Is there really no full featured and good quality partitionning tool for Linux?

---

### Post by plors on 2006-02-06
I guess you 'moved' it by copying the partition (or the data). That way it looks like a move but was instead the same as the way i described earlier.

---

### Post by lol on 2006-02-06
mm, I am still not convinced. 'Moving' the partition the way you describe it means that you must have enough free space to move all the data on the new partition.

Modifying the following partitions:
/dev/hda1 -> vfat 10GB, containing 5GB of data
/dev/hda2 -> ext3 10GB, containing 8GB of data
like this:
/dev/hda1 -> vfat 6GB
/dev/hda2 -> ext3 14GB
would therefore be impossible...

If this is really the case, then ext3 really sucks. I was reading comparisons on filesystems not long ago, nobody ever mentioned this, but in my opinion, this would be a HUGE flaw in the filesystem, and the best reason ever not to use it...

Another reason why I am a bit sceptical, is that ext3 is nothing more than ext2 with a journal. And it is quite easy to convert ext3 back to ext2 (it takes 2s, the time to delete the journal, more or less). I am quite positive that PM is able to move an ext2 filesystem. So, it should be easy to delete the journal, treat the partition as ext2 and then recreate a journal... Any decent software should be able to handle this much, or I am wrong?

---

### Post by plors on 2006-02-06
nobody ever said the same wouldn't go for ext2....
afaik this goes for most filesystems (including ntfs and the reiser* filesystems).

imho this is not a real problem since there aren't really that much people who needs to repartition every week (or every year for that matter).
I have done tons of setups/installations and most of the time i create partitions just once..

The problem you describe is hard, but not impossible to solve. To make things easier one can even use a temporary disk.

What i'd like to know is if PM is indeed able to do this. I've never heard of this before and i'd like to see it confirmed.

---

### Post by lol on 2006-02-09
> What i'd like to know is if PM is indeed able to do this. I've never heard of this before and i'd like to see it confirmed.

I should be able to confirm it this WE. A friend of mine has the current partitioning scheme :
/dev/hda1 vfat 15GB windows
/dev/hda3 ext3 5GB linux
and he want to allocate more space to linux. In his case, there is no other solution than to move the beginning of the ext3 partition (which is at the end of the disk).

I will let you know if we were able to do it...

---

### Post by lol on 2006-02-12
All right, so I can confirm that partition magic is able to move the beginning of an ext3 partition, without any problem.

Therefore I will say it again: it's really pitiful that no Linux is able to do that. 

I can already imagine the reaction of my friends when I will have to ask them if I can plug my HD in their computer to repartition it... They will have a good laugh!

---

### Post by plors on 2006-09-04
i just released gparted with movesupport for all filesystems, have fun :-)

[http://gparted.sourceforge.net/news.php](http://gparted.sourceforge.net/news.php)

---

### Post by gerbman on 2006-09-04
Good news! :)

---

