---
title: "SD Card reading as the wrong size"
date: 2006-08-10
forum: Desktop Environments
---

### Post by a-v0id on 2006-08-10
Hi guys,

  I only just noticed this problem having been all evening working out how to encode a divx film for my pda. Having encoded the flick into a managable size for the pda I decided to throw the file onto my card reader onto the SD card and thus onto my PDA.

  After much wincing and whining at the size problem of whether or not 209MB would fit onto a 256MB SD card (post format), I realized that the card was reading on my machine as a 39.7MB card. I am fairly confident that the card works perfectly (size wise) on other operating systems, but due to the lack of other operating systems nearby I have not been able to check.

Has anyone had this problem before, and/or does anyone have any tips for me to check or correct my problem?

Cheers again

a-v0id

---

### Post by ahave2005 on 2006-08-10
I've been there, it's a pretty irritating problem. Check your card for hidden files (.Trash). The worst thing that could happen, is a vmware server install with ((windows)) to format the card. For some reason gparted are not getting things right with flash memory cards.(or external usb discs not linux fs's)

I haven't looked into a workaround for this, allthough I'm sure it exist. I have a vmware xp on my server, for reasons like this, and exchange at work.

I'm pretty sure I found a solution to this just before my vacation a month ago, but can't remember what i did. (.Trash) I might have formatted it with XP, but I'm pretty sure i just deleted some trash files.

---

### Post by a-v0id on 2006-08-11
Regrettably, I don't have VMWare. I checked for .Trash and found that there isn't any hidden directories on the disk.

Are you saying "gparted" is what I should read up on?

Cheers,

a-v0id

---

### Post by maniacmusician on 2006-08-11
he's saying gparted doesn't work so well with flash drives. maybe qtparted (a KDE program) does it better? i am not sure. just a suggestion on my part, i would confirm it with someone else if i were you.

---

### Post by a-v0id on 2006-08-13
QTParted did do the job for me. Thanks maniacmusician! Although only could format to FAT16.

Thanks again.

For those wanting to know:

```
sudo apt-get install qtparted
```

Applications > System Tools > QTParted

Select your media card, and format the partition in to FAT16 again.

Crude, I know, but it solved my problem.

*Edit*
Further thinking, it may pay to empty the Wastebasket .... and save you having to download and install QTParted. :p

---

