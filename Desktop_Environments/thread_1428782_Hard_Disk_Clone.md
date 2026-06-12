---
title: "Hard Disk Clone"
date: 2010-03-13
forum: Desktop Environments
---

### Post by Ostrichmeat on 2010-03-13
Hi guys,

Long time reader, first time poster and all that! Looking for some help with a new hard disk I've got, spent the last two days trying to get it all sorted and failed miserably...

Basically, I've got a 500GB HDD at the moment, running the following:

sda1: Windows XP (32 bit) 180GB
sda2: Windows Vista (32 bit) 180GB
sda3: 50GB partition with varying installations, currently empty
sda4: extended partition
sda5: Ubuntu 8.04 (32 bit) 54GB
sda6: Linux-swap 1GB

Now, I want the following on my new 2TB HDD:

sda1: Windows XP 500GB
sda2: Windows Vista 500GB
sda3: 50GB partition, empty for now
sda4: extended partition
sda5: Ubuntu 9.10 (64 bit) 200GB
sda6: Linux-swap 1GB

So, I set about sorting that out. I used GParted Live CD (most recent version) to copy and paste the sda1 partition to sdb1, then booted to sda2's Vista, and resized sdb1 to 500GB. 

Then restarted to GParted Live, copied sda2 to sdb2, then booted to Vista to resize to 500GB.

I created the 50GB partition sdb3 and left it at that, then created the extended partition, then created an ext3 logical partition for Ubuntu 9.10, formatted it again to ext3 with an Inode size of 128 (I want to use GRUB-legacy - just can't get my head around GRUB2, and I've tried hard!).

Finally, created a linux-swap partition

The remainder of the space on the 2TB HDD (1.82TB when you ask an OS) I am going to allocate at a different time.

The problem I'm having is that the Windows partitions are corrupting during copying/resizing. I cannot understand why.

I know Vista won't tolerate just being copied and resized, but I have run the start up recovery and not had much joy. The first time I started this off, it worked okay, but the next time it would boot but it wouldn't recognise the keyboard or mouse.

XP would boot, but as soon as you logged in, it would log you out again - but keyboard and mouse fine.

Ubuntu seems to be okay, but I've probably reinstalled it between 15 and 20 times due to getting GRUB-legacy to work. The main reason I want to do all this is to get a larger Ubuntu partition so that I can use it more. That's why I bought the damned HDD to begin with!

Any suggestions? I've read so many topics on this, but not been able to get anywhere. All I ask is please no unconstructive replies regarding the Windows installations - I have no choice but to use both XP and Vista for work purposes. Ubuntu is my 'leisure' OS. I have a reasonable linux knowledge, starting from Mandrake in 2003 - since then, I've used SuSE, Red Hat (before the days of Fedora) and gentoo.

Thanks!

---

### Post by coffeecat on 2010-03-13
> **Ostrichmeat said:**
> The problem I'm having is that the Windows partitions are corrupting during copying/resizing. I cannot understand why.

I don't think it's so much a matter of Windows corrupting, but of some sort of MS anti-piracy measure. It can tell if it's been copied from one disc/partition to another and refuses to co-operate. To be honest I don't understand the details.

What you need to do is to use some sort of imaging/cloning app. The two widely-used commercial ones are Norton Ghost (no experience of) and Acronis True Image. I had very good results with an earlier version of Acronis. I was able to clone directly from one disc to another when I wanted to change HDs, and you can also clone with their backup to image utility. You image to USB drive/DVDs/another partition, then boot up with live CD (which you prepare with Acronis) and restore from image.

If you don't want to spend any money :wink:, another app I've had good experience with is Macrium Reflect:

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

It doesn't do direct cloning, and one limitation not shared by Acronis is that you can't make an image and then restore that image to a smaller partition, even if there is plenty of room. (Not a problem for you though.) Apart from that I've successfully restored both Vista and Windows 7 (RC) with it. One bonus apart from being free is that the live CD you prepare with Macrium is Linux-based. \o/

> **Ostrichmeat said:**
> All I ask is please no unconstructive replies regarding the Windows installations - I have no choice but to use both XP and Vista for work purposes. Ubuntu is my 'leisure' OS. I have a reasonable linux knowledge, starting from Mandrake in 2003 - since then, I've used SuSE, Red Hat (before the days of Fedora) and gentoo.

That's all right. You don't have to justify using Windows on this forum. MS bashing is discouraged and most people are relaxed about what OSs other people choose to use. "Whatever works for you" is a phrase I often see on this forum. If anyone is discourteous to you about using Windows, please use the 'report abuse' button to bring this to the attention of the moderators. They try to encourage a friendly, tolerant attitude (spirit of Ubuntu) and MS or other-distro or MacOS bashing is just not in that spirit.

Good luck!

---

### Post by Ostrichmeat on 2010-03-13
Thanks for that, your help is most appreciated. I shall have a look into those and see what I can do.

As for the MS bashing - as you can probably guess, I've been active in other linux communities before and seen a lot of it going on. Can't say I particularly understand it personally, but there you go. I have noticed in these boards that people tend to be a lot friendlier (hence why I posed the question here, as well as because I'm a big Ubuntu convert!)

THanks again.

---

