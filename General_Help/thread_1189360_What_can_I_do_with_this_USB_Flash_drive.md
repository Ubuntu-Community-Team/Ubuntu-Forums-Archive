---
title: "What can I do with this USB Flash drive?"
date: 2009-06-16
forum: General Help
---

### Post by Craigy90 on 2009-06-16
Hey everyone,

I have a 32GB flash drive that was working fine for a while (maybe 8-10 months). Then, I started getting "Read Only Drive" errors when using it in Windows. There is no write protection on the disk, and the error was intermittent, so I copied all of my data off the drive and tried to format it using Windows. That didn't work, so I brought it over to Ubuntu and tried to format using gparted. Again, no success. I then tried using badblocks to find errors on the disk, here is the output:

```

sudo badblocks -svw /dev/sdc
Checking for bad blocks in read-write mode
From block 0 to 31588351
Testing with pattern 0xaa: 15792128done, 16:20 elapsed
15792248
15792368
15792488
15792608
15792728
15792848
15792968
15793088
15793208
15793328
15793448
15793568
15793688
15793808
15793928
15794048
15794168done, 16:21 elapsed
15794288
15794408
15794528
15794648
15794768
15794888
15795008
15795128
15795248
15795368
15795488
15795608
15795728
15795848
15795968
15796088
15796208
15796328
15796448
15796568
15796688
15796808
15796928
15797048
15797168
15797288
15797408done, 16:22 elapsed
15797528
15797648
15797768
15797888
15798008
15798128
15798248
15798368
15798488
15798608
15798728
15798848
15798968
15799088
15799208
15799328
15799448
15799568
15799688
15799808
15799928
15800048
15800168
15800288
15800408
15800528
15800648done, 16:23 elapsed
15800768
15800888
15801008
15801128
15801248
15801368
15801488
15801608
15801728
15801848
15801968
15802088
15802208
15802328
15802448
15802568
15802688
15802808
15802928
15803048
15803168
15803288
15803408
15803528
15803648
15803768
15803888done, 16:24 elapsed
15804008
15804128
15804248
15804368
15804488
15804608
15804728
15804848
15804968
15805088
15805208
15805328
15805448
15805568
15805688
15805808


```

and then it hangs, with the read/write light on the usb drive not flashing or anything.

So my theory is, something messes up when you try to write to a part of the disk near the 50% point. There is no way that I can get it replaced, short of buying a new one. I could throw it away, but you know... it's 32GB! I could format the drive, using a 15GB partition that does not use the broken bits and I could also try to make a partition after the broken place, if I could find where it is writable again, and if it is only this one place. In any case, I will not be storing ANY important information on it in the future.

So my question is, what would you do? Is there a way to somehow tell the drive that those bad sectors do not exist, or some other way to get around this problem? Also, why does badblocks simply stop working, instead of giving an error?

Thanks, and better luck to your flash drives.

---

### Post by synapsys on 2009-06-16
Flash drives only have a limited number of writes in their lifetime. It's probably toast. What brand is it?

---

### Post by Craigy90 on 2009-06-16
It is an A-DATA myflash. Yeah, I think it's pretty much a lost cause at this point.

---

### Post by wpshooter on 2009-06-16
What happened when you tried to format it with Gparted ?

Also, what FS type did you try to format it as ?

I would try either FAT16 or FAT32.

---

### Post by Craigy90 on 2009-06-16
Well, the format went fine, but I would get errors when trying to write to the drive. It was formatted with fat32.

---

### Post by theozzlives on 2009-06-16
When I bought my first XT computer, with a MFM Half Height 20 MB 5 1/4" HD, and upgraded up to 640K RAM, I lost everything! Granted 20 MB ain't much now, but was a lot then.

I learned that no storage media is 100% reliable. That's why I tell my customers not to store important files on any one media. In other words BACKUP OFTEN.

I hope you got everything off your USB stick, it's now ready for the trash (unless you wanna use it for a keychain).

---

### Post by Craigy90 on 2009-06-16
Yes, you are absolutely right, and that is sound advice. I did get all my stuff off, (nothing was stored there that wasn't backed up somewhere else as well) and the drive will inevitably get thrown away (or disassembled, it must be pretty cool inside).

Ran badblocks again, and it got to 15839048 before failing. Weird.

---

### Post by sedawk on 2009-06-16
As far as I understood flash drives have some internal logic
to remap broken blocks, e.g. while block 1,2,3, and 4 might
be fine, the broken block 5 might be damaged and the block
has been disabled. Whenever you read block 5 the block
might already be mapped to a backup block (somewhere behind
the 32 GB boundary).

So your flash drive might be out of spare blocks to use as backup
and any error somewhere on the disk will kill your data.
So when badblocks reports blocks 10,11 and 12 to be broken, they
might be located anywhere on the disk. Trying to create
partitions around these "physically broken areas" therefore
is impossible, as there is no such area.

One idea could be to store stuff on that disk with lots of
redundancy and error correcting code, so you could still
use 16 GB or 8 GB of the flash drive.
Some people thought about developing special file systems for
flash drives, but I haven't checked the status lately.

---

### Post by Fully216 on 2009-06-16
I am surprised that no one has mentioned the fact it still might be under warranty.  While it is true that flash drive have a certain life span, if it has been under a year, it is likely a manufacturing defect not a life cycle issue.  You might consider contacting the manufacturer and seeing what they are willing to do.  I am sure they will be interested in their drives are failing too soon.

---

### Post by HermanAB on 2009-06-16
32GB flash sticks are $42 at Wal-Mart.

---

### Post by raymondh on 2009-06-16
> **theozzlives said:**
> I learned that no storage media is 100% reliable. That's why I tell my customers not to store important files on any one media. In other words BACKUP OFTEN.


+1 ... that's why I CD my personal media and data

---

### Post by Fully216 on 2009-06-16
Regarding vectoring out bad data, this is true when the drive is manufactured.  Before the drive is finalized, the drive will be tested and if there are large segments that fail testing, they will be vectored out.  So a 4 GB drive still could be sold, but at a smaller size for example.  This way the drive is not completely waisted and the memory company still gets some return on their product which they spent money making.

There is way to protect against read errors as well, as you mention.  Parity checks do this for a small binary series, but do not work well once the size of the data set becomes large as the possible errors increase.

Vectoring out bad data sectors pretty much can only be done when the drive is manufactured, at least to my knowledge.  However, someone that is more of an expert in the field might be able to tell you more.

---

### Post by theozzlives on 2009-06-16
Just throw the stick away, I wouldn't trust my data on unstable media.

---

### Post by Craigy90 on 2009-06-17
Thanks for all the replies!

> **sedawk said:**
> As far as I understood flash drives have some internal logic
to remap broken blocks, e.g. while block 1,2,3, and 4 might
be fine, the broken block 5 might be damaged and the block
has been disabled. Whenever you read block 5 the block
might already be mapped to a backup block (somewhere behind
the 32 GB boundary).

So your flash drive might be out of spare blocks to use as backup
and any error somewhere on the disk will kill your data.
So when badblocks reports blocks 10,11 and 12 to be broken, they
might be located anywhere on the disk. Trying to create
partitions around these "physically broken areas" therefore
is impossible, as there is no such area.

That is cool, I did not know that it worked like that. It is somewhat surprising that so many blocks would fail all at once though. I guess it was a bad unit.

> **Fully216 said:**
> I am surprised that no one has mentioned the fact it still might be under warranty.  While it is true that flash drive have a certain life span, if it has been under a year, it is likely a manufacturing defect not a life cycle issue.  You might consider contacting the manufacturer and seeing what they are willing to do.  I am sure they will be interested in their drives are failing too soon.

No, I don't believe that it is under warranty. I will double-check that though.

> **HermanAB said:**
> 32GB flash sticks are $42 at Wal-Mart.

Yeah, that's true. Mostly I just wanted to know if, from a purely technical standpoint, there was a way to 'fix' the drive.

> **Fully216 said:**
> Regarding vectoring out bad data, this is true when the drive is manufactured.  Before the drive is finalized, the drive will be tested and if there are large segments that fail testing, they will be vectored out.  So a 4 GB drive still could be sold, but at a smaller size for example.  This way the drive is not completely waisted and the memory company still gets some return on their product which they spent money making.

There is way to protect against read errors as well, as you mention.  Parity checks do this for a small binary series, but do not work well once the size of the data set becomes large as the possible errors increase.

Vectoring out bad data sectors pretty much can only be done when the drive is manufactured, at least to my knowledge.  However, someone that is more of an expert in the field might be able to tell you more.

Thanks, that's very informative.

> **theozzlives said:**
> Just throw the stick away, I wouldn't trust my data on unstable media.

I definitely wouldn't use it for storing anything that wasn't backed up elsewhere, and will be disposing of it. Sound advice. :)

---

