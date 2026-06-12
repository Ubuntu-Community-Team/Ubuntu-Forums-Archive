---
title: "How to create Backup Partition"
date: 2009-04-19
forum: General Help
---

### Post by snorbens on 2009-04-19
Hi,
Please excuse me if this has been asked and replied to before.
I did try and search the forums, but if the answer is there, I must have missed it, so put it down to my advancing years.

Now, I have a 230Gb hdd with Ubuntu 9.04 and a swap partition of 5Gb. I wish to create a partition for backup purposes.

When I have tried previously with gparted it seemed to corrupt ubuntu so I am hoping for an idiot's (that would be me) guide into doing it.

As I have said whenever I used gparted before, I thought that I did everything right but apparently not. Even yesterday I tried and then had to completely reinstall ubuntu.

Any advice please

---

### Post by cinematography on 2009-04-19
What kind of filesystems are you trying to work with? ext3? reiserfs? And if you don't know, typing 'mount' into a terminal should provide the information. I ask this because some filesystems can't be made smaller.

---

### Post by snorbens on 2009-04-19
> **cinematography said:**
> What kind of filesystems are you trying to work with? ext3? reiserfs? And if you don't know, typing 'mount' into a terminal should provide the information. I ask this because some filesystems can't be made smaller.

The main, and largest partition is ext3 and all I need to do is make a partition on that one, just for backup purposes, using sbackup.

I just do not want to go in blazing and create a partition that my cock-up my existing setup.

Thanks for your reply.

---

### Post by cinematography on 2009-04-19
I don't see any reason why the Gnome Partition shouldn't be able to do the trick. You could be able to shrink that partition, and then create the backup partition after it, without any problems. Does the partition that you want to shrink have much free space available?

---

### Post by snorbens on 2009-04-19
> **cinematography said:**
> I don't see any reason why the Gnome Partition shouldn't be able to do the trick. You could be able to shrink that partition, and then create the backup partition after it, without any problems. Does the partition that you want to shrink have much free space available?

Yes it has 221Gb free. It is just that I am nervous I expect, after the mess I apparently made with gparted before.

I just want to make sure that I can do it safely without corrupting my current installation.

Thanks

---

### Post by cinematography on 2009-04-19
> **snorbens said:**
> Yes it has 221Gb free. It is just that I am nervous I expect, after the mess I apparently made with gparted before.

I just want to make sure that I can do it safely without corrupting my current installation.

Thanks
I've resized partitions with gparted before and everything went okay, but I'm not an expert, and I'm not sure if there are some other questions that I should be asking before you proceed with the resize, so I'm going to leave the follow up to my fellow Ubuntu users. I would hate to recommend the wrong approach for you.

But one thing that you should always do before any kind of formatting and resizing... Make backups!

---

### Post by snorbens on 2009-04-19
Thanks for your help........I will keep drinking my pots of coffee and maybe gain the courage to give it another go!:)

As I said I have messed up when using gparted before but it was probably me not paying attention, but as a newbie I am trying to be cautious.

---

### Post by -kg- on 2009-04-19
My suggestion would be to read the following guide on partitioning:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

This will give you a basic guide on partitioning operations.

You should be able to safely resize an ext3 partition with a GPartEd Live CD or use GPartEd from the Ubuntu Live CD.  If you had created an ext4 partition, then you might have had problems (but likely not with the partition editor provided with the Jaunty Live CD/DVD), but since you've indicated that the partition is ext3, there should be no problem whatsoever.

Now, you have a 4 Primary partition limit.  How many partitions do you currently have?  If there are already 4 Primary partitions (and have no Extended partition), you will not be able to create any more partitions.  You will have to delete one of the partitions (the swap partition is a good candidate) and create an Extended partition.  You will then be able to recreate your swap partition and any other partitions you require inside the Extended partition as Logical partitions.

Read the information provided on the page(s) linked to above, and you should have a good grounding in partitioning operations.  Any more questions, and just post back and I or someone will guide you further.

BTW:  A 5 GB Swap partition?  How much RAM do you have?  You only really need 1 1/2 times the amount of RAM you have and, depending on what you're doing with the computer, the more RAM you have, actually the less Swap space you need (unless you're doing a lot of video editing or some type of CAD projects).  I have ! GB of RAM on my desktop and 2 GB of RAM on my laptop.  I have never used my Swap file on either of these computers yet.  You very likely don't need anywhere near 5 GB of Swap.

But if you have all that much space on your hard drive(s), then it won't hurt anything.

P.S. - I just re-read...if you have 221 GB free on your hard drive, then you have no reason at all to resize anything.  That amount of free space is more than enough to install Ubuntu and absolutely any software to do anything you want to do with Ubuntu.  Both my installations (desktop and laptop) take about 1/4 of what you have available.

---

### Post by snorbens on 2009-04-19
Thanks very much your reply, very helpful and re-assuring.

The partitions I have are sda 1 ext3 at 227Gb. sda2 extended and sda5 linux-swap.

The size of the swap partition was determined by ubuntu when I installed it.

So I should be able to shrink sda1 and then create another primary partition for my backups?

I will also check out the link after my third pot of coffee!;)

Sorry to appear on the stupid side but as I have been only using Windows until a couple of weeks ago it is a big learning curve for me. And as I am nearing 60yrs of age I am probably a lot slower,grey matter wise, than I was a few years ago.

---

### Post by snorbens on 2009-04-19
Thanks for all your help...

I have managed to create a partition for my backups, and it appears that I did it without messing everything up.

I now have an extra 10Gb partition to use as I wish:D

All I need to know now is how to mark this as solved

Cheers

---

### Post by -kg- on 2009-04-19
> All I need to know now is how to mark this as solved

A while back the forums server crashed, and in the interest of stability the ability to mark a thread as SOLVED was taken out, along with the ability to THANK and to count those THANKS.

I have recently seen some threads that have been marked SOLVED again, but I am unaware if the ability to mark a post thusly has been returned, since I haven't posted a request for help in some time now.

Actually, I just found [a thread that answers this question]("http://ubuntuforums.org/showthread.php?t=1044714"), so the ability to mark a thread as SOLVED is still not available.  I have seen a few posts lately that are marked thusly, so there must be a way to do it.

Perhaps editing your original post and then adding SOLVED to the title line?

Yep.  Just edit your first post, then select the "Advanced" button below the editing Window.  You will be able to edit the Title line as is necessary.

---

