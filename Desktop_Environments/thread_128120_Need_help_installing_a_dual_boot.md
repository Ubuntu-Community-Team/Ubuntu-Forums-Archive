---
title: "Need help installing a dual boot?"
date: 2006-02-10
forum: Desktop Environments
---

### Post by jacatone on 2006-02-10
Could someone direct me to a set of instructions for installing a dual boot with WinXP Home and Kubuntu 5.10? I have Partition Magic, would it be easier using that? Does Kubuntu use Lilo as it's OS selector? Thanks.

---

### Post by FlakJacket on 2006-02-10
I used partition magic when i did my install. Best option IMO.  In PM on XP I resized my NTFS partition with XP on it.  Then I created a 15 gig Ext3 partition (you can make it however big you want for your root partition) a 512 gig swap partition and a 125 mb (i think) Ext3 partition for /boot.  Then when I was installing Kubuntu I selected manually setup partition table.  Assigned the 15 gig one to / the 512 swap should already be set to swap and the 125 meg to /boot.  Installed without a hitch. Then use aysiu's tut for mounting your windows partition if you want [here](http://www.psychocats.net/linux/mountwindows.php).

Hope that helps,
Flak

EDIT: I also set the /boot to bootable I assumed this made sense but I don't know if it was necessary

---

### Post by jacatone on 2006-02-11
What is IMO?

---

### Post by Neo Ex on 2006-02-11
In My Opinion ;) 
I've read around that it's not a great thing using Partition Magic to create ext3 partitions. I've preferred to let Ubuntu creates the partition it needs, after resizing the Windows partitions with Partition Magic.

---

### Post by aysiu on 2006-02-11
The fifth link of my signature walks you through setting up a dual boot (including partitioning) and includes screenshots.

---

### Post by oatmeal on 2006-02-11
[QUOTE=aysiu]The fifth link of my signature walks you through setting up a dual boot (including partitioning) and includes screenshots.[/QUOTE]

You and your signature rock. I came here looking for answers to those questions. and they're all right there?  

Well, hell. No need to go any further. :)

I registered just to say thanks.

Thanks. :KS

---

### Post by cuda70383 on 2006-02-11
that's the guide i used for my kubuntu & xp dual boot and it works perfect!!!  that's what i'm using now on my toshiba tecra 9000 and am connected wirelessly.  

my only "issue" is trying to set up a wireless share w/my desktop.

---

