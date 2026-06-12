---
title: "Help with partition and making a swap partition"
date: 2005-12-15
forum: General Help
---

### Post by Sofoklis243 on 2005-12-15
Hi folks,
I am a complete newbie in linux world. Of course I had a friend talk me into this...well here's the thing. I have both windows xp and ubuntu on the computer now. I used partition magic in windows to make two partitions. Stupidly enough I didn't make a Swap partition in windows. Then I installed Ubuntu on the partition I had set off for it. Well, that's fine. But now I really would like to make a Swap partition for Linux...could anyone help me with that? I probably need someone to tell me with table spoons...I would appreciate any help I could get.

---

### Post by Domie on 2005-12-15
It has been a long time since I did that, FAT32 was still the standard in Winland.

I see you also use Partition Magic. Back then, I defragmented  my logical station in the extended partition, so everything would be stored in the beginning. Now look at the free space. Resize the partition in PQMagic to what you want, but leave some free space left. Wait... Now you can make a new partition and can format it to swap.

Hope this lookback in time can help you.

---

### Post by Sofoklis243 on 2005-12-15
Hey again,
thanks for ur reply. I've now gone back in Windows, created a Swap file for linux in Partition Magic. Is that it? Or do I  have to do something in Linux as well for it to know it's really there?

---

### Post by mikeymouse on 2005-12-15
why not just make some free space and let Ubuntu do the rest.
I deleted a partition on my 80 gig drive with parition magic, left it as free space and let ubuntu do all ... I always like to let the other guy do the work if he is able..(g).
 hope this helps
 mikeymouse

---

### Post by tlc on 2005-12-15
Are you sure the Ubuntu installer didn't create a /swap for you anyway?

I'm at work so can't check but I think, "fdisk -l" or "fdisk -a" should list all your partitions. You may well already have one.

---

### Post by Sofoklis243 on 2005-12-16
Hi thanks for ur help so far, but my problem is that when I installed Ubuntu I said no to install swap partition at the time (yes it was stupid:-)) because at that time i only had two partitions one for windows and one for linux. So I think I need to do this manually now...I have however now created a swap partition in partition magic in windows...i just wonder if ubuntu knows it is there just like that or if i have to do anything....but it seems as if I can use the fdisk command to set it up right?

---

### Post by alamba on 2005-12-16
I dont have a straight shot solution to give you here but might be able to point you in the right direction.

I just read a post on this forum an hr or so ago regarding a similar issue. The guy there had a very small swap partition and he was able to supplement it by creating a swap file and then mounting it is /etc/fstab.

Evidently it worked wonders for him. Search around in the forum and you should be able to find it.

Akshay

---

### Post by Domie on 2005-12-17
[QUOTE=tlc]Are you sure the Ubuntu installer didn't create a /swap for you anyway?

I'm at work so can't check but I think, "fdisk -l" or "fdisk -a" should list all your partitions. You may well already have one.[/QUOTE]

You too? Man, we're gonna get fired ;-)

Do you mean let Ubuntu do the work when being installed?

---

### Post by poptones on 2005-12-17
Just create a swapfile in your root ubuntu partition.

dd if=/dev/zero of=/swap.img bs=1024k count=255

That will create a 255MB file in your root partition. You can then mount it as a swapfile by adding the line to your /etc/fstab:

/swap.img        none    swap    swap    0       0

Once you have that type in a terminal

sudo /etc/init.d/mountall.sh start

and it will automagically mount your new swap "partition."

---

### Post by Sofoklis243 on 2005-12-20
Thanks, when I typed
dd if=/dev/zero of=/swap.img bs=1024k count=255

I got this: 
255+0 records in
255+0 records out
267386880 bytes transferred in 21.985964 seconds (12161708 bytes/sec)

Is that correct? And I also wonder how do I extend the partition already have? I have an ext3 partition, and a parition for windows, but i also have empty space that's not available for neither windows nor linux, how can i make this available for linux?

I am also not allowed to perform this command: /swap.img none swap swap 0 0
And what do u mean by add it to /etc/fstab?

---

### Post by poptones on 2005-12-20
Sorry, I missed that part about you already having a partition you could use. Go ahead and delete the file you made with the "dd" command, then post here the result of this command: sudo fdisk -l

---

