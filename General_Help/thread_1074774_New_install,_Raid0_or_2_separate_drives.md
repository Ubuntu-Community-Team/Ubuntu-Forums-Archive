---
title: "New install, Raid0 or 2 separate drives?"
date: 2009-02-19
forum: General Help
---

### Post by UranUtan on 2009-02-19
Hi,

I would like to install Ubuntu 8.10 x64 on a computer currently running Vista x64.

Hardware specs: CPU Core 2 E8400, Raid0, striping two SATA drives of 500 GB. The RAID firmware is built into the chipset (nForce 630i / GeForce 7100) of the motherboard.

The entire 1 TB storage space had been formatted NTFS. I can free one extended partition to install Ubuntu. My initial plan was to use dual boot with the option to install GRUB in the Ubuntu partition and not in MBR. Then I will use a multi-boot manager to start either Vista or Ububtu.

However, I could never get the Ububtu Live CD or Alternate CD to recognize the Raid0 unit. Gparted only see two blank hard drives, ignoring the existing partition layout.

So now I downgrade my ambition to a poorman version. I will give up on multi boot and will just install Ubuntu 8.10 alone, reformatting everything. 

**What do you suggest to use the two SATA drives? As two independent drives? Or Raid0 striping two disks?**

BTW for those of you who has experience in Raid0 in Linux, is there any performance gain which is worth the hassle? And is Raid0 driver reliable under Linux?

Thanks very much for any help.

---

### Post by Yashiro on 2009-02-19
Raid0 for your operating system and files without a full backup procedure is stupid idea. 
It has double the chance of failure and the performance gains are minimal. Of course this is only one persons opinion. :P

Using 'motherboard raid' is also known as 'fakeraid' in so far as it also depends on drivers to work correctly. As such using a fakeraid for dual booting Win/Linux can work but can also be problematic. (uses dmraid on Linux)

I would install Windows on one drive onto a small partition. Leave the rest of that drive unformatted for now. Then install Ubuntu on the other HD. Maximum flexibility and you will always have a bootable OS.

---

### Post by jerome1232 on 2009-02-19
I would setup the raid0 just to learn more about working with a raid :) But as the poster above me said keep backups, especially with that setup since if one device fails it ruins the whole raid.

Using lvm would probably be a good idea as well for the flexibility.

offtopic, I don't see how raid0 is even a "raid" there's no redundancy there...

---

### Post by jerrrys on 2009-02-19
offtopic, I don't see how raid0 is even a "raid" there's no redundancy there...

i may be wrong about this, but wasn't it random array of inexpensive drives, redundancy was added as an afterthought..

---

### Post by makisupa123 on 2009-02-19
> **jerrrys said:**
> offtopic, I don't see how raid0 is even a "raid" there's no redundancy there...

i may be wrong about this, but wasn't it random array of inexpensive drives, redundancy was added as an afterthought..

It was originally "redundant".  The term 'RAID0' did not really exists when the term was coined and was later used to describe the striping scenario (sans redundancy).

see:
[http://www.cs.cmu.edu/~garth/RAIDpaper/Patterson88.pdf](http://www.cs.cmu.edu/~garth/RAIDpaper/Patterson88.pdf)

for all the geeky details.

--Mak

---

### Post by UranUtan on 2009-02-19
> **Yashiro said:**
> Raid0 for your operating system and files without a full backup procedure is stupid idea. 
It has double the chance of failure and the performance gains are minimal. Of course this is only one persons opinion. :P

Agreed on the backup and x2 chance of failure. Not agreed on performance. Here is a detailed benchmark to prove the point:
**Chipset Serial ATA and RAID performance compared. Whose arrays are faster?** [http://techreport.com/articles.x/9124/1](http://techreport.com/articles.x/9124/1)

The article shows that Raid0 has sometimes same performance than a single drive but for half of the benchmarks, Raid0 is faster than a single drive. From my current experience, the write speed is definitely faster.

However, I am not looking for performance. Flexibility, reduced risks and easy maintenance definitely weight more for my case. The Raid0 I was using was mainly for curiosity and indeed if is not flexible, for example, I cannot take out one drive and mount it in an USB enclosure or in another computer and expect to read data. It needs its other Raid "buddy" drives. In case of change like what I am trying to do, thw two units must be handled together and on top of this there is potential headache with Linux driver issue. 

So for now, I'd rather go with the solution you suggested (two independant drives, no Raid).

---

### Post by jerrrys on 2009-02-19
and i though i knew everything..thanks makisupa123

---

### Post by apmcd47 on 2009-02-19
With only two disks I'd personally either go for mirroring (RAID1?) or use the disks separately.

Andrew

---

### Post by Therion on 2009-02-19
Drive 1: Operating system 
Drive 2: Data, Backups, etc. 

Dual-drive rigs are the ONLY way to fly, in my opinion.

---

### Post by Slim Odds on 2009-02-19
For servers, RAID1 (or other "redundant" types) is great. But for a home machine (desktop or laptop) I think that it's overkill. I mean, do you really need to be able to hot swap a drive?

Also, RAID0 is fantastic. Even on servers the hard drives are normally a HUGE bottleneck. The increased performance of stripping should not be underestimated.

Even on my home machine (which is a little old and underpowered CPU wise) I use RAID0 with a pair of SATA drives that the difference is dramatic.

When working with large audio or video files it's a must.

Also of note, I'm using software RAID even thought my motherboard had "RAID" (the crappy kind). It was pretty easy to get setup and pretty much invisible once running.

---

### Post by UranUtan on 2009-02-19
> **Slim Odds said:**
> For servers, RAID1 (or other "redundant" types) is great. But for a home machine (desktop or laptop) I think that it's overkill. I mean, do you really need to be able to hot swap a drive?

Also, RAID0 is fantastic. Even on servers the hard drives are normally a HUGE bottleneck. The increased performance of stripping should not be underestimated.

Even on my home machine (which is a little old and underpowered CPU wise) I use RAID0 with a pair of SATA drives that the difference is dramatic.

When working with large audio or video files it's a must.

Also of note, I'm using software RAID even thought my motherboard had "RAID" (the crappy kind). It was pretty easy to get setup and pretty much invisible once running.

Would you at least agree on the x2 risk potential? One hard drive failure and your entire Raid unit is fried. 

Besides that, I would like to give the Raid0 under Ubuntu a try, I am curious to see if it really works. Hoping that the operation would be simple enough. What did you do so that the Ubuntu boot CD recognize you Raid0 unit?

---

### Post by Slim Odds on 2009-02-19
> **UranUtan said:**
> Would you at least agree on the x2 risk potential? One hard drive failure and your entire Raid unit is fried.

Yes, but I don't think that is a big deal. There are always trade-offs. To get double the performance, you get some minor risk.

Larger server systems often use a nested array. See this the section on nested arrays on this page: [http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

> **UranUtan said:**
> Besides that, I would like to give the Raid0 under Ubuntu a try, I am curious to see if it really works. Hoping that the operation would be simple enough. What did you do so that the Ubuntu boot CD recognize you Raid0 unit?

LOL, if it didn't work you'd be hearing a lot of squawking about it.

If you really want to use the hardware on the motherboard (which is usually not a "true" RAID), then there are a bunch of forum posts about that (just search for fakeRaid).

I am not dual booting, so I took the simpler approach of using software RAID. I don't think that there's any real advantage to using the fakeRaid stuff (if it were a true RAID where it is totally transparent in the hardware, then OK). The software RAID works fine.

I used the alternate install CD which has mdadm by default.

---

