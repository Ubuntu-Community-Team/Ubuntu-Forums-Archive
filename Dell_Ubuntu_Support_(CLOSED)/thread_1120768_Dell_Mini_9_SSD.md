---
title: "Dell Mini 9 SSD"
date: 2009-04-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lenamtl on 2009-04-09
Hi,

I have a question to Dell Mini9/Ubuntu owners:

Do you had black screen of death on booting / operating system not found? (HD is not responding anymore)

This issue occur 2 months after starting using Dell Mini9 with Windows XP, there is a lot of people who had this issue and I'm wondering if this issue occur also to Ubuntu users...

I got this issue and planning to switch to Ubuntu OS instead of Windows... I don't want to start over every 2 months...

Maybe it is a batch of bad SSD HD or it's an issue whith Windows on SSD, I just don't know.

Thanks

---

### Post by anjilslaire on 2009-04-09
I've had mine loaded with 8.10 since late December, no issues.

---

### Post by ugm6hr on 2009-04-09
> **lenamtl said:**
> This issue occur 2 months after starting using Dell Mini9 with Windows XP, there is a lot of people who had this issue

Really?  Wow.

I've had mine about 2 months now; hope it behaves itself.

Fine so far though.

---

### Post by notwen on 2009-04-09
> **lenamtl said:**
> Hi,

I have a question to Dell Mini9/Ubuntu owners:

Do you had black screen of death on booting / operating system not found? (HD is not responding anymore)

This issue occur 2 months after starting using Dell Mini9 with Windows XP, there is a lot of people who had this issue and I'm wondering if this issue occur also to Ubuntu users...

I got this issue and planning to switch to Ubuntu OS instead of Windows... I don't want to start over every 2 months...

Maybe it is a batch of bad SSD HD or it's an issue whith Windows on SSD, I just don't know.

Thanks

Have you contacted Dell's customer support to see if they have had multiple instances of this behavior from the Minis shipped in your area?  

If there is a lot of ppl having this issue(and complaining to Dell) I'm sure Dell has investigated the issue and hopefully identified/resolved it.  If indeed the SSD is bad, installing Ubuntu on it won't make it's reliability/performance any better than w/ Windows.  I would contact them first off before you install Ubuntu and possibly have the SSD give you problems again down the road.  Just a thought.  =]

---

### Post by armandh on 2009-04-09
no problem but I have had hdd(s) that fail xp and work fine with Ubuntu

---

### Post by lenamtl on 2009-04-09
I have contacted Dell, the tech said that she have no clue, she told me to check on Google :-k

But I know that several users got replacement HD from Dell.
check on this forum : [http://mydellmini.com/forum](http://mydellmini.com/forum)

In the Bios I see the HD, but the size = 0
So I can boot from this hd and I cannot format it because size =0

The other thing is I have bough it through BestBuy and in that case Dell they saying call BestBuy and when I called BestBuy they  saying call Dell.. BestBuy finally said ok to check my computer...

Anyhow for now I have ordered a new ssd hd, I will see if this will happened again. 

Maybe this time I will install Ubuntu.

---

### Post by mtbsoft on 2009-04-09
Had mine dual-booting XP and 8.10 for about four months, no problems at all.  Sounds like a duff SSD, good luck with the new one.  Surely if the thing is under warranty, they should be replacing it though.

---

### Post by armandh on 2009-04-10
first down load a partition editor

g-parted
or
parted magic

ubuntu 8.04.1 or 8.10 live has it built in

size = 0 may be no partition

if a partition editor won't show the drive it may be bad

or it shows the drive but no partition
[a windows virus might have deleted the partition or screwed the 0 sector / mbr]

---

### Post by lenamtl on 2009-04-11
I'm not able to reinstall windows and or repair it.
So I took a original Ubuntu CD 8.10 and try to install.
I was suprise that it detect the size (not exactly 8go but 7.7 go)

Everything went fine except during the install I got a message:
(I'm french so this is not the exact message but a translation)
If I do 2 partition:
The system file creation fail on partition 1 of SCSI1 (0,0,0) (sda).

If I create 1 partition:
creating exchange space fails on partion 5 of SCSI1 (0,0,0) (sda)

I follow this tutorial:
[http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html) 

any clue?

---

### Post by armandh on 2009-04-11
since you are installing 8.10 not the original 8.04 I would still try a partition editor to clear the HDD of anything that might be interfering with the setup

---

### Post by lenamtl on 2009-04-11
ok I'll give a try

thanks

---

### Post by lenamtl on 2009-04-12
Hi thanks for your patience,

Ok yesterday I have run **pmagic**
I saw disk healt = failed.
(disk will fail very soon)

red:
prefail attribute
old age attribute
I don't know exactly what theses status mean but I guess it not good.

The partition editor don't find anything, how come Ubuntu installer can see my drive  and partition but not XP or pmagic?

Also I have see the wipe tools and want to use it before sending my defect HD to Dell, I tried the 1st option but it is really slow 200mb-per hour..As the ssd is only 8g I can't use the last selection 'secure' that seems faster.

Is there a faster wiping tool for ssd?

Thanks

---

### Post by brimlar on 2009-04-13
You might also want to consider flashing your bios to the latest rev (A04 at this time) if you haven't done so already.

Apparently a lot of bugfixes have been implemented in their bios updates.

---

### Post by armandh on 2009-04-13
sounds like failed drive to me

It can find a drive but cannot find further levels
[such as there are or are not any partitions]

---

