---
title: "Simple Questions on Partition Options"
date: 2009-03-15
forum: General Help
---

### Post by The_Lost_World on 2009-03-15
Hey guys! TLW here. No, I still haven't installed Ubuntu. I was very busy for a while, and I tend to procrastinate on big things that involve messing with my hard drive. :P

Anyways, what happened with my Ubuntu install, is that I had 68 GB of unallocated space, so I thought I would use the "largest unallocated free space" option, and that would be convenient. Unfortunately, I'm having a problem where when I select that option, it still says it will use ALL of my ENTIRE hard disk! It looks like this:

[IMG]http://i538.photobucket.com/albums/ff341/the_cake_is_a_lie/100percent.png[/IMG]

But that's okay. I'll use manual. However I have a few questions.

Well, first of all I should probably show you a screenshot of the Partition Manager to show what I have going on here: 

[IMG]http://i538.photobucket.com/albums/ff341/the_cake_is_a_lie/PartitionManagerScreenshot.png[/IMG]

Okay, so you can see there that I have 68 GB of unallocated space. So I decided I was going to give 60 GB to root ("/") and 8 GB to swap ("swap").

However, there's a lot of options in the manual screen! :( Perhaps you guys could help me out? Here are two screenshots of the screen, and the options.

Here is the manual partitioning screen in the installer:

[IMG]http://i538.photobucket.com/albums/ff341/the_cake_is_a_lie/PartitioningScreen.png[/IMG]

And here is a screenshot of all the options...

[IMG]http://i538.photobucket.com/albums/ff341/the_cake_is_a_lie/PartitioningOptions.png[/IMG]

So, to sum it up, here are my basic questions:


**1. Is 60 GB for root and 8 GB for swap (I have 1 GB RAM but I am going to upgrade to 2 GB soon) a good amount? Should I have less for swap?**

**2. Should root and swap be primary partitions, or logical partitions?**

**3. Should BOTH root AND swap be ext3 formatted?**

**4. Should I set the "Location for new partition" on them to "Beginning" or "End"?**

**5. What should be the mount point on the root and swap partitions? Should root be "/" and swap "swap"?**


Thank you so much for reading, and please post if you have anything to say! :)

---

### Post by fatbotgw on 2009-03-15
1)  Those should be fine for sizes.  My auto-partitioned install has an 11GB swap.
2)  If you're only going to have 4 total partitions then it doesn't matter.  However, if you're going to change your partition size later I would make one large 60GB logical and put the / and swap in there.  Ubuntu shouldn't care either way.
3)  / -> ext3  and  swap -> "linux-swap"
4) Beginning (which means "at the beginning of the free space")
5) Yes, root is "/" and swap is "swap"

---

### Post by The_Lost_World on 2009-03-16
> **fatbotgw said:**
> 1)  Those should be fine for sizes.  My auto-partitioned install has an 11GB swap.
2)  If you're only going to have 4 total partitions then it doesn't matter.  However, if you're going to change your partition size later I would make one large 60GB logical and put the / and swap in there.  Ubuntu shouldn't care either way.
3)  / -> ext3  and  swap -> "linux-swap"
4) Beginning (which means "at the beginning of the free space")
5) Yes, root is "/" and swap is "swap"

Thanks a bunch! ^_^

---

### Post by The_Lost_World on 2009-03-16
For safety, can anyone else confirm what he said about the partitions being okay logical or primary? And is it really okay to put both the swap and root in the same partition?

No offense fatbotgw, I'm just the paranoid type. :P

---

### Post by plucky on 2009-03-16
> For safety, can anyone else confirm what he said about the partitions being okay logical or primary? 

If you make them primary,then you will have the maximum number of partitions you can have on the disk.

If you want to have more partitions,it is best to use logical.The /root and /swap partitions can be logical. 

You might think of having a separate /home partition as well in the future.

> And is it really okay to put both the swap and root in the same partition?

/swap and /root will not be on the same partition,they will be separate logical partitions within an extended partition.The /root partition will be ext3 and the /swap will be formatted as linux-swap.

The /swap partition only need to be the size of your RAM,so 2GB is sufficient and some would say 1GB is plenty.

[color=red]Please do not post large pictures ,upload as thumbnails,because if you are on a slow dial-up line,it takes forever to read your posts.[/color]


Good Luck

---

### Post by fatbotgw on 2009-03-16
> **The_Lost_World said:**
> For safety, can anyone else confirm what he said about the partitions being okay logical or primary? And is it really okay to put both the swap and root in the same partition?

No offense fatbotgw, I'm just the paranoid type. :P

No offense taken.  I'd want as much info as I could get from as many sources as is reasonable.  Especially if I was worried about messing something up.

Also, this might help: [Partitioning for Ubuntu]("https://help.ubuntu.com/8.04/installation-guide/i386/partitioning.html")

---

### Post by The_Lost_World on 2009-03-16
> If you want to have more partitions,it is best to use logical.The /root and /swap partitions can be logical.
I don't think I'm going to have any more partitions, but it's always good to have the ability to have them. However, are primary partitions superior to logical ones in performance or another factor?

> You might think of having a separate /home partition as well in the future.
What kind of functionality would this add? Would it be easier to manage my personal files if I made a /home partition? How big should the "/home" and "/" partitions be if I wanted to add a /home partition?

Also, the /home partition would be ext3, correct?

> /swap and /root will not be on the same partition,they will be separate logical partitions within an extended partition.The /root partition will be ext3 and the /swap will be formatted as linux-swap.
Wait... so I take the unallocated space and create the root and swap partitions (and maybe /home), right? Or am I supposed to do something more complicated?

> The /swap partition only need to be the size of your RAM,so 2GB is sufficient and some would say 1GB is plenty. 
Then I will go for 2 GB.

---

### Post by plucky on 2009-03-17
> I don't think I'm going to have any more partitions, but it's always good to have the ability to have them. However, are primary partitions superior to logical ones in performance or another factor?


No

> What kind of functionality would this add? Would it be easier to manage my personal files if I made a /home partition? How big should the "/home" and "/" partitions be if I wanted to add a /home partition?

The /home partition contains all the configuration files for the software you are using,plus all your personal files.If you have to re-install,and you don't format your /home partition,then all your software configurations will remain the same.

But you should still have backups to do the same job if you don't have a separate /home.

My /root partition is 10GB with 3GB used.Give the rest to /home.

> Also, the /home partition would be ext3, correct? Yes

> Wait... so I take the unallocated space and create the root and swap partitions (and maybe /home), right? Or am I supposed to do something more complicated?

Yes,or if it is just /root and /swap,leave it unallocated and let the installer sort it out for you.


Good Luck

---

### Post by Jouke74 on 2009-03-17
Just to be on the safe side: Make a backup of all your important data before repartitioning your harddrive. :popcorn:

---

### Post by The_Lost_World on 2009-03-17
> The /home partition contains all the configuration files for the software you are using,plus all your personal files.If you have to re-install,and you don't format your /home partition,then all your software configurations will remain the same.

But you should still have backups to do the same job if you don't have a separate /home.

My /root partition is 10GB with 3GB used.Give the rest to /home.
Ah, I see, thanks.

> Yes,or if it is just /root and /swap,leave it unallocated and let the installer sort it out for you.
Nah, I'm doing it manually, because the guided "use largest available space" option is not working.

> Just to be on the safe side: Make a backup of all your important data before repartitioning your harddrive. 
Yea, lol. I have a HUGE external drive, actually, so should I back up my entire hard disk, or just my personal stuff?

---

### Post by The_Lost_World on 2009-04-30
Hey, a tiny but very important question here, please answer.

I see people calling the partitions "/home" and "/swap", but also calling the swap partition just "swap". How should I set them when partitioning? As "/<example>" or "<example>"?

Thank you!

---

