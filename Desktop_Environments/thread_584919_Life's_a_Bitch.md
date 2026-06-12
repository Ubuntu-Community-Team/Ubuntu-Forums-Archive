---
title: "Life's a Bitch"
date: 2007-10-21
forum: Desktop Environments
---

### Post by Geffers on 2007-10-21
I thought I'd share this interesting little story.

Decided to buy a 2.5" HD and external enclosure so that I could have a wee play with some Ubuntu set ups.

Drive installation into external box took about 30 seconds, plugged it in to my Linux box, got some whirring sounds but nothing else.

Typed gparted into command window but program could not be found.

Try it in XP laptop thought I, plugged it in, USB device detected, showed on Device manager but not in My Computer or Computer Management.

Put an old 2.5 drive into enclosure and plugged in, device detected and ready to use BUT it did not show on My Computer so it was not ready to use. Tried a powered USB hub in case my old 2.5 drive was drawing too much current, still no show.

Decided to try both old and new 2.5 drives in a powered IDE to USB adapter I had, old drive worked OK but not new one.

I had another bright idea, try new 2.5 drive in IDE connection on motherboard of desktop, after a mistake with master and slave positions it showed as 534MB, only 39.5GB short of the expected 40GB.

Looks like a dodgy drive but now comes the "Icing on the Cake", my desktop will not boot, says it is not a bootable hard drive.

It used to be a dual boot (Ubuntu and Win98) 20GB hard drive with some data, it now an unformatted 20GB drive.

So, great day, bought a drive that don't work and trying to fix it ended up with two drives that don't work; whole day wasted.

It looks like the Partition Table disappeared somewhere.

Fortunately no data lost, just time.

Geffers

---

### Post by PmDematagoda on 2007-10-21
For your gparted problem, install it using:-

```
sudo apt-get install gparted
```

About your booting problem, change the boot order and HDD order in your BIOS.

About your portable HDD problem, is it an NTFS drive?

And please choose a more suitable title before you start a thread.

---

