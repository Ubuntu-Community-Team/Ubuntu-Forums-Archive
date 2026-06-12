---
title: "Not better than zero"
date: 2009-03-03
forum: General Help
---

### Post by MountainX on 2009-03-03
I've been searching google for how to wipe all data (including MBR and partition tables and metadata that doesn't seem to want to go away) from my disk (so I can install fresh).

My drive is 1.5 TB. If urandom takes 2-3 days for a 300GB drive, I don't even want to try it with a 1.5TB drive. I need a better/faster way. 

I found the following tip and I'd like to know how to do it. See "Not better than zero" below.
> 
**[badblocks and random numbers]("http://www.hermann-uwe.de/blog/howto-disk-encryption-with-dm-crypt-luks-and-debian#comment-13784")**

              ...dd with /dev/urandom takes 2-3 days on my Pentium M 1.6 GHz and a 300 GB USB hard drive. And the CPU load is at 100% constantly, both my laptop and the drive get *quite* hot...
     
                            Mon, 2006-04-03 23:05 — DavidH (not verified)              **[Not better than zero]("http://www.hermann-uwe.de/blog/howto-disk-encryption-with-dm-crypt-luks-and-debian#comment-13900")**

             Well...the problem is that it would be just as easy to distinguish unused blocks.
 Find any commonly recurring block, and there you go...
 A better, asm-optimized solution would be to setup a temporary cryptmount (for example with a random key from /dev/random and using aes256 cipher) and dd /dev/zero to that.
 Provided that aes is not a weak cipher, which seems unlikely, the output should be indistinguishable from random data, and the operation should be quite a bit faster than urandom.




So how would I go about using this method?

---

### Post by LegendofTom on 2009-03-03
Have you tried low level formatting?

---

### Post by MountainX on 2009-03-03
> **LegendofTom said:**
> Have you tried low level formatting?

No. I was told that low level formatting of a modern HDD is not possible outside the factory.

If I can do it, how would I do it?

---

### Post by DGortze380 on 2009-03-03
killdisc

it may take upwards of a day on a drive that size... sorry, fact of life.

---

### Post by Slim Odds on 2009-03-03
Well, for one thing, a Pentium M 1.6G is a dog.

Secondly, I think that it is unnecessary to call /dev/urandom 300 billion times to wipe a drive. You could just create a block of random data of a smaller size that then just repeatedly use that. Or several random blocks repeated.

---

### Post by MountainX on 2009-03-03
> **Slim Odds said:**
> Secondly, I think that it is unnecessary to call /dev/urandon 300 billion times to wipe a drive. You could just create a block of random data of a smaller size that then just repeatedly use that. Or several random blocks repeated.

That probably won't accomplish the goal. Someone could easily find your real data that way. It would be no different from writing zeros (which also doesn't accomplish the security goal).

---

### Post by heindsight on 2009-03-03
You shouldn't need to do all that just to reinstall. Simply repartitioning, and reformatting should be quite sufficient.

EDIT:
Of course if you want to sell or give away the machine and you want to securely erase any data first, you could use shred which should be installed by default. Your best bet would probably be to boot a live cd and then shred the hard drive. Of course on a disk that big it will take a long time, but any method of securely erasing your disk will.

---

### Post by Slim Odds on 2009-03-03
> **MountainX said:**
> That probably won't accomplish the goal. Someone could easily find your real data that way. It would be no different from writing zeros (which also doesn't accomplish the security goal).

How so?

If you create one random sector worth of data and write that to every sector on the disk. That's just as good as writing a different random sector worth of data to every sector on the disk.

Of course, you do it multiple times for each sector.

---

### Post by Slim Odds on 2009-03-03
> **heindsight said:**
> You shouldn't need to do all that just to reinstall. Simply repartitioning, and reformatting should be quite sufficient.

Yah, but where's the argument in that?   :P

---

### Post by Rallg on 2009-03-03
Are you trying to destroy data for privacy reasons, or simply blank out the hard drive (write all zeroes)?

Assuming that you simply want to write all zeroes, try this: Boot to a live Ubuntu on USB (or CD). If it mounts any partition on the hard drive, unmount the partitions. Open the Partition Editor, get rid of all partitions on the hard drive, and give it a new device label. make note of what the device location is (let us say that it is sdX). In Terminal:

sudo dd if=/dev/zero of=/dev/sdX bs=512

If that is refused, then try

sudo -s
(it switches you to root)
dd if=/dev/zero of=/dev/sdX bs=512

In principle, it should write 0 everywhere, including the (former) MBR.
If that does not work, then sorry for my poor advice!

Note to others who find this thread: the above dd command should NEVER be used as written, unless you intend to wipe your drive. There are other ways to use dd that have safe effects.

---

### Post by MountainX on 2009-03-03
> **heindsight said:**
> You shouldn't need to do all that just to reinstall. Simply repartitioning, and reformatting should be quite sufficient.

You may think so, but this is not true (at least for me, on this computer). As I said, I alredy repartitioned and reformatted. Apparently, there is metadata on the disks outside of the partition and I want to get rid of that now, before I have data on here that I really care about. 

Now is the time to get this right.

---

### Post by MountainX on 2009-03-03
> **Slim Odds said:**
> How so?

If you create one random sector worth of data and write that to every sector on the disk. That's just as good as writing a different random sector worth of data to every sector on the disk.

Of course, you do it multiple times for each sector.

It is all about patterns. Your method will produce a non-random pattern -- a pattern that repeats. Never mind that each small part of that pattern is random, it is a pattern none-the-less and it will defeat your security attempts. But this is off topic.

**EDIT: this assumes you will be subsequently writing encrypted data to the disk.**

I am asking about how to do a very specific command using dd with a cipher where the guy explained it briefly but didn't describe exactly how to do it. See post #1 above.

---

### Post by Rallg on 2009-03-03
Did you try post #10 ?

Incidentally, if your time is valuable and security is the problem, consider incinerating your present drive, and get a new one. Guaranteed to work! :P

---

### Post by MountainX on 2009-03-03
> **Rallg said:**
> Did you try post #10 ?

Incidentally, if your time is valuable and security is the problem, consider incinerating your present drive, and get a new one. Guaranteed to work! :P

Yes, I have done that a couple times.
I even wrote a blog post about it: [http://davestechshop.net/linux-how-to-uninstall-grub](http://davestechshop.net/linux-how-to-uninstall-grub)

That only hits the start of the partition. Apparently some metadata is written to the end of the partition or elsewhere.

When I use dd as stated, it does get rid of the error. But as soon as I create a new partition, the error is back.

BTW, this is a brand new disk. I'm not going to throw it away just because I tried to install Ubuntu to it. If I have to throw away my hard disk every time I attempt to install Ubuntu, this is a very, very bad thing!

---

### Post by Slim Odds on 2009-03-03
> **MountainX said:**
> That only hits the start of the partition. Apparently some metadata is written to the end of the partition or elsewhere.

What "metadata" are you talking about?

Disks are made of sectors. Sectors have data.

Metadata is a concept within a file system (for example). There is no metadata in raw disk data.

---

### Post by MountainX on 2009-03-03
> **Slim Odds said:**
> 
Metadata is a concept within a file system (for example). There is no metadata in raw disk data.

Apparently you don't know about raid and LVM, both of which put metadata on the disk outside the file system.

---

### Post by Slim Odds on 2009-03-03
> **MountainX said:**
> Apparently you don't know about raid and LVM, both of which put metadata on the disk outside the file system.

LOL

Apparently I do. I use RAID0.

So am I to understand that you think that RAID and LVM hide some of your personal information in their metadata?

---

### Post by MountainX on 2009-03-03
> **Slim Odds said:**
> LOL

Do you think that RAID and LVM hide some of your personal information in their metadata?

No.

---

