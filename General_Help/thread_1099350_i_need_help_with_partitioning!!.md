---
title: "i need help with partitioning!!"
date: 2009-03-18
forum: General Help
---

### Post by xsaulx on 2009-03-18
this is what my hard drive looks like right now!
[IMG]http://i40.tinypic.com/117bjwi.png[/IMG]

xp -1
ubuntu -2
swap -3
windows7 -4

its a mess! i had no clue there was a 4 partition limit! haha
so now i have a huge unallocated space! 291gb!!! and i wanna try to get my hard drive organized better!

i want to make my ubuntu partition bigger, since i use ubuntu more then windows now! =D
and i want to have a partition for music and one for shared files that i can access from all of my os'.

i was thinkin if i boot from my live cd i can delete the extended swap partion. and make the others in a new extended partition... but then would the swap work from there?

---

### Post by jadhav333 on 2009-03-18
Suggested Partition Structure
=============================
/dev/sda1   ntfs..............................WindowsXP

/dev/sda2   ntfs..............................Windows7

/dev/sda3   
......extended
....../dev/sda5  ext3.......................Ubuntu Root
....../dev/sda6  ext3.......................Ubuntu Home
....../dev/sda7  swap.....................Ubuntu Swap

/dev/sda4   ext3.............................Shared Data files

Make sure that:
1) you back up critical data before you get on with the re-partitioning.

2) you have all the installable CDs & driver disks with you handy

3) you will additionally require a free application Ext2 IFS ([http://www.fs-driver.org/](http://www.fs-driver.org/)) to access the shared drive partition. I have recommended the ext3 filesystem for the shared drive becoz its journaling system keeps data secure from crashes.

4) You install Windows first.

---

### Post by circa82 on 2009-03-18
The problem you're going to run into with your current setup is that your windows 7 partition sits between the free space and the partitions you want to allocate that free space to. If you're alright with removing Windows 7, it should be pretty easy. If you're not, that will make it a lot harder.

If you remove the Windows 7 partition ( sda4 ), you should also remove the swap partition and extended partition. You'll have one large chunk of free space, then you can allocate whatever amount you want to Ubuntu. Then create a new (primary) partition for Windows 7 - if you still want it. Then create an extended partition and under that extended partition, create the swap, music, and storage partitions. However, that all requires you to get rid of Windows 7.

---

### Post by xsaulx on 2009-03-18
Thanx for the ideas!
I'm thinkin I can just remove ubuntu and swap, add that space to windows 7. And then reinstall with the layout in the first reply. Since ubuntu installs easier then windows!!

But if I remove ubuntu will it remove grub from the mbr? I just got this triple boot working in grub so I wanna keep that!

---

### Post by circa82 on 2009-03-18
Removing Ubuntu won't remove GRUB from the mbr. However; you'll still need to reinstall it since Windows 7 not Ubuntu, will be on sda2.

---

### Post by xsaulx on 2009-03-18
> **circa82 said:**
> Removing Ubuntu won't remove GRUB from the mbr. However; you'll still need to reinstall it since Windows 7 not Ubuntu, will be on sda2.

so if i reinstall grub it'll configure boot setup for me? at least for ubuntu?
i already know how to setup grub for winxp/7..

---

### Post by circa82 on 2009-03-18
Sorry, ignore my previous post. Though it's true, when you go to reinstall Ubuntu, it will setup GRUB for you. It will detect itself, and should detect both Windows OSes as well. Sorry, forgot you were reinstalling Ubuntu from scratch.

---

### Post by meierfra. on 2009-03-18
If you move the start point of the Win 7 partition you will also have to reconfigure Win 7 boot loader. 

Nothing wrong with your current plan, and if  you would like to have a  larger  Ubuntu partition, that's exactly how I would to it.
 But  here are a couple of suggestion how to avoid reinstalling any of the OSs

1) Delete the current swap and extended partitions and add the freed space to the Ubuntu partition. Then use the unallocated space at the end to create an  extended partition with a new swap partition and a new logical partition.

2)  Convert your Win 7 partition to a logical partition (just asked, and I show you how to do that). Then you will be able use the unallocated space at the end to create  a new logical partition.

---

### Post by xsaulx on 2009-03-20
well this is what i have so far..
i deleted the extended/swap partition.
made a new extended partition, with a logical for my music, and swap. keeping some space if i wanna make a logical for other files..or maybe to try that instant on os. presto[http://www.prestomypc.com/getpresto_early_signup.php?utm_campaign=Get%20Presto%20-%20Boot%20Your%20PC%20in%20Seconds&utm_content=nilay@engadget.com&utm_medium=Email&utm_source=VerticalResponse&utm_term=HTML%20Version%20-%20Image%20Link%201]("http://www.prestomypc.com/getpresto_early_signup.php?utm_campaign=Get%20Presto%20-%20Boot%20Your%20PC%20in%20Seconds&utm_content=nilay@engadget.com&utm_medium=Email&utm_source=VerticalResponse&utm_term=HTML%20Version%20-%20Image%20Link%201")

i think i'm gonna move the win7 partition(sda4) more towards the back and add the empty space to ubuntu but for some reason i couldn't edit sda2(ubuntu) with gpartded even from a live usb. why is that?

[IMG]http://i39.tinypic.com/wl9dky.png[/IMG]

---

### Post by meierfra. on 2009-03-20
> and add the empty space to ubuntu but for some reason i couldn't edit sda2(ubuntu) 

You need to unmount the ubuntu partition first (Just right click it  and choose unmount)

> i'm gonna move the win7 partition(sda4) m

The yellow triangle on your win 7 partitions, means that gparted thinks that there is something wrong with it. So I'm pretty sure  that gparted won't let you move the win 7 partition. Right click  win7 and choose "check". You should get some kind error message and maybe some suggestions how to fix the problem.

Ntfs is a much better file system  than fat32 and since the linux driver for the ntfs are very reliable by now, I don't see any reason to use Fat32.

Instead of moving win 7 and increasing Ubuntu, you might think about creating a separate home partition.

---

### Post by xsaulx on 2009-03-20
> **meierfra. said:**
> You need to unmount the ubuntu partition first (Just right click it  and choose unmount)

i tried, it gave me an error and couldn't unmount. and i don't think it should've mounted anything since it was a live version.


> **meierfra. said:**
> 
The yellow triangle on your win 7 partitions, means that gparted thinks that there is something wrong with it. So I'm pretty sure  that gparted won't let you move the win 7 partition. Right click  win7 and choose "check". You should get some kind error message and maybe some suggestions how to fix the problem.

"check" is un-clickable.:(

> **meierfra. said:**
> 
Ntfs is a much better file system  than fat32 and since the linux driver for the ntfs are very reliable by now, I don't see any reason to use Fat32.

yea but ntfs gets locked if windows crashes! it annoys me when that happens to my external drive ntfs. i was gonna use ext3 like the first post suggested but i'm not sure how the support is for windows.

> **meierfra. said:**
> 
Instead of moving win 7 and increasing Ubuntu, you might think about creating a separate home partition.
i don't think i need really need anymore space for ubuntu, i moved a few files to my new media partition and that gave me enough space but i would still like to add the old swap space to ubuntu if i can. i'll try again and see exactly what the error was.

---

### Post by meierfra. on 2009-03-20
> i tried, it gave me an error and couldn't unmount.
Strange. What was the error message?

>  and i don't think it should've mounted anything since it was a live version.

The Ubuntu LiveCD likes to mount partitions automatically. Or are you using the Gparted LiveCD?   

> "check" is un-clickable

You might have to install "ntfsprogs" for "check" to work:
```
sudo apt-get install ntfsprogs
```

Or get the Gparted LiveCD. It often works better than the gparted on the Ubuntu LiveCD.


> yea but ntfs gets locked if windows crashes! 


I still think ntfs is the better option. But as long as you don't want to work with files larger than 4GB, Fat32 should be ok, too.


Is your new  swap partition working correctly? You can check with 

```
 free 
```

---

### Post by xsaulx on 2009-03-20
> **meierfra. said:**
> Strange. What was the error message?
don't remember..but im downloading gparted live right now and i'll check again.

> **meierfra. said:**
> 
You might have to installe "ntfsprogs" for "check" to work:

installed it! triangle went away! all options are avalible! =D

> **meierfra. said:**
> 
I still think ntfs is the better option. But as long as you don't want to work with files larger than 4GB, Fat32 should be ok, too.
only for music! mp3. acc. i don't have anysongs that long!! 

> **meierfra. said:**
> 
Is your new  swap partition working correctly? You can check with 
forgot about that! turned it on in gparted..its working now...
i'll see if it mounts automatically next time..


oh and another quick question..
moving my win7 partition wont mess with my boot setup right?
just so its next to sda6,extended..so i can add the space to ubuntu..

---

### Post by meierfra. on 2009-03-22
> moving my win7 partition wont mess with my boot setup right?
just so its next to sda6,extended..so i can add the space to ubuntu..


 Probably Win7 will no longer boot if you move its start point. 
Usually it is recommended to use the Win7 disk management to partition a Win7 partition. But I tried that once and it would let be move the start point.   So you might  have to use gparted.

After you moved Win7 and you can't boot into Win 7 any more,  you will have to fix the Win 7 boot loader.   Boot from the Win 7 CD and select "Repair Computer". It probably  will offer you to fix a start up problem. Accept the offer and  the CD should fix the problem for your.

The Win 7 CD might get confused about "bootmgr" and "/Boot", which were left on the XP partition  when you separated the XP and Win 7 boot loader. So  I suggest to delete, rename or move both of those. (But of course don't touch the ones on the Win 7 partition)


PS: I usually to not look at a thread, unless it has a new post. So instead of editing a post, you should post a new message.

---

### Post by xsaulx on 2009-03-22
thats more work then i wanna do lol..
i cleaned up my ubuntu partition and got a coulple gbs..i'm just gonna add the gig for my old swap to it..
add the rest of the space to win7....

THANX FOR ALL THE HELP!! :D

---

### Post by meierfra. on 2009-03-22
Sorry for pessimistic view. I had some bad experience with moving the start points of Windows partition. But my experience doesn't really match what have seen seen in here in the forum. It least see whether the Win 7 disk management lets you move the Win 7 partition. If that works, you shouldn't have any problems.

Is you swap working?

---

