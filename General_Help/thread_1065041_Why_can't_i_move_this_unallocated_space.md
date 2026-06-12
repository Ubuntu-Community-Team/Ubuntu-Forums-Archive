---
title: "Why can't i move this unallocated space?"
date: 2009-02-09
forum: General Help
---

### Post by epqr on 2009-02-09
Why can't i move unallocated space to /dev/sda1? I know it has this warning triangle on it, but thats not the issue. I have tried to do this with a live CD and it still doesn't work.

The thing is i just reduced /dev/sda4 (see pic). But i can't seem to move the space i reduced anywhere else. Why is this? is there a way i can move this space to "sda1"? iv'e already moved some other unallocated space there. But they showed up as "two different unallocated spaces" :p. And now gparted doesnt allow me to expand it more (again i do this with a live cd, i know i can expand it, but it doesn't work with this space)

Thanks! 


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=102760&stc=1&d=1234210780[/IMG]

---

### Post by Therion on 2009-02-09
Not 100% sure about this, but I think your "unallocated" space needs to be adjacent to the partition you want to expand to include the "unallocated space".

In short, the two "pieces" need to be adjacent before you can "merge" them, if you will.

Does that make sense?

---

### Post by personjerry on 2009-02-09
you need to force it to mount before gedit will allow you to edit the partition.
> sudo mkdir /media/ntfs_partition
sudo mount -force sda1 /media/ntfs_partition

---

### Post by epqr on 2009-02-09
> **personjerry said:**
> you need to force it to mount before gedit will allow you to edit the partition.

As i stated the problem is not being able to edit the partition, but to add the unallocated space to it. If I got what you meant right.

> **Therion said:**
> Not 100% sure about this, but I think your "unallocated" space needs to be adjacent to the partition you want to expand to include the "unallocated space".

In short, the two "pieces" need to be adjacent before you can "merge" them, if you will.

Does that make sense?



kinda yeah:P

Any idea on how to do this? preferably without having to format the partition.

---

### Post by estyles on 2009-02-09
You need to move all the partitions toward the back of the drive.  It will take a long time, and I'd be a little afraid of doing it without backup essential data first.  You *shouldn't* have any problems, but a random lockup or power outage in the middle of moving partitions is death.

So, edit /dev/sda4 and put "0" space after the patition.  Then edit sda3 to take up the rest of the space, then move the partitions inside sda3 like you moved sda4, and finally shrink sda3 and move sda2.  Then your space will be adjacent to sda1 and you can grow sda1.

For the record, I have no idea what the poster who mentioned gedit it talking about.

---

### Post by personjerry on 2009-02-09
editing a partition includes adding free space to it. e.g., try adding the free space to one of your partitions that have been mounted, then remove the free space if that works.
if it doesn't, then I guess it has to be adjacent

---

### Post by epqr on 2009-02-09
> **estyles said:**
> You need to move all the partitions toward the back of the drive.  It will take a long time, and I'd be a little afraid of doing it without backup essential data first.  You *shouldn't* have any problems, but a random lockup or power outage in the middle of moving partitions is death.

So, edit /dev/sda4 and put "0" space after the patition.  Then edit sda3 to take up the rest of the space, then move the partitions inside sda3 like you moved sda4, and finally shrink sda3 and move sda2.  Then your space will be adjacent to sda1 and you can grow sda1.

For the record, I have no idea what the poster who mentioned gedit it talking about.

Thanks man:) I'll it out soon :) when you say long, you mean long like 1/2hour-1hour or like 4-5 hours?

---

### Post by estyles on 2009-02-09
> **epqr said:**
> Thanks man:) I'll it out soon :) when you say long, you mean long like 1/2hour-1hour or like 4-5 hours?

Depends on a number of things, but somewhere in between.  Moving one 15 GB partition, IIRC, took me about an hour.

---

