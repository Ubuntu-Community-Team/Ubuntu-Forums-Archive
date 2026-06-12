---
title: "Need advice: SD Card as Storage disk on dell  mini 9"
date: 2009-07-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vickoxy on 2009-07-20
Hi,
i want to buy some SD-Card ([http://geizhals.at/a297971.html](http://geizhals.at/a297971.html)) that should be my extra Storage disk for my PDF books and documents. Can someone tell me how fast is reading from such cards, or is it better to move PDF book every time on dell´s SSD? 

Any advice how to get better performance or how to properly use SD cards....?

Dell Mini 9, 2 GB RAM, 8GB SSD, Ubuntu 9.04 Desktop Edition :D
Thanks

---

### Post by ugm6hr on 2009-07-20
I use an SDHC card for all file saving on my mini.

I use ext3 format, since it is always plugged into my Mini, and occasionally used to transfer files to my (Ubuntu) laptop.

I can recommend it.

I use an 8GB card, since 16GB+ are a lot more expensive at the moment, and there is nothing stopping you from having multiple cards to swap out.

I would recommend labelling them so they are auto-mounted at e.g. /media/sdhome etc rather than the default /media/disk.

---

### Post by vickoxy on 2009-07-20
> **ugm6hr said:**
> I use an SDHC card for all file saving on my mini.

I use ext3 format, since it is always plugged into my Mini, and occasionally used to transfer files to my (Ubuntu) laptop.

I can recommend it.

I use an 8GB card, since 16GB+ are a lot more expensive at the moment, and there is nothing stopping you from having multiple cards to swap out.

I would recommend labelling them so they are auto-mounted at e.g. /media/sdhome etc rather than the default /media/disk.


I think that i do not understand *labelling*-maybe little how to/what is it? Well, i want to buy 16 or 32 GB and it should stay most of the time plugged in my dell mini 9, but i want to have the option to remove it when i want it...

Does Class 4 or 6 means anything (performance)?

ugm6hr, thanks for answer!

---

### Post by ugm6hr on 2009-07-20
The Class is supposed to represent max transfer rates.  However, I haven't found any problem with any, and actually replaced (a repeatedly faulty) Transcend Class 6 with a Sandisk Class 2 with no noticeable difference.

The label (sdhome in example below) is what the computer sees the disk name as.  To format an sd in Ubuntu with ext3:

```
sudo cfdisk /dev/mmcblk0 
```

Change partition format to type 83 (Linux), Save & Exit

```
sudo mkfs.ext3 -L sdhome /dev/mmcblk0p1 
```

I then changed the permissions to 777 (i.e. allow everyone to read, write and execute) using thunar (Xfce file manager), since I keep forgetting how to chmod using Terminal.

You can then still mount and unmount / eject as necessary.  But be aware that ext3 will only be read by Linux systems (i.e. not MS or Mac without additional drivers).

There are lots of people who say ext3 (with journalling) is not recommended for SD cards, but I figure they are cheap, so I'll replace it if it dies.  And I always keep backups.  If you are concerned, use ext2 instead.

---

### Post by vickoxy on 2009-07-20
Thanks! :popcorn:

---

### Post by vickoxy on 2009-07-20
Still one question-if i leave card as it is (no ext2, ext3 or labelling) would the performance be the same as with ext*formatting?

---

### Post by ugm6hr on 2009-07-20
> **vickoxy said:**
> Still one question-if i leave card as it is (no ext2, ext3 or labelling) would the performance be the same as with ext*formatting?

Probably, yes.  The data transfer rate is independent of format.

Remember that most are FAT32, which cannot tolerate any files larger than 4GB, although this is often not an issue with SD.

However, unless you use Mac or MS, I don't see any good reason to use FAT.

---

### Post by vickoxy on 2009-07-20
> **ugm6hr said:**
> Probably, yes.  The data transfer rate is independent of format.

Remember that most are FAT32, which cannot tolerate any files larger than 4GB, although this is often not an issue with SD.

However, unless you use Mac or MS, I don't see any good reason to use FAT.

Yes i know (about FAT32)-so, when i talk about performance i just want to know is there any difference in reading (especially PDF books that have 400-500 pages)-data transfering is not issue for me. Still i prefer to have it in FAT because i copy/paste/work with MS, Mac and Linux, but this card would mainly be stick in my dell mini9... As i remember i have no file bigger then 1GB...

---

### Post by ugm6hr on 2009-07-20
> **vickoxy said:**
> when i talk about performance i just want to know is there any difference in reading (especially PDF books that have 400-500 pages)

I don't think there is any difference, but then this is a more technical question than my knowledge extends to.

---

### Post by vickoxy on 2009-07-20
> **ugm6hr said:**
> I don't think there is any difference, but then this is a more technical question than my knowledge extends to.

Thank you for answers, i also think that -if there is any difference - it would be merely noticable for me as average user. I should just go for 16/32 GB Card... :P

---

### Post by vickoxy on 2009-07-28
NEED Advice _again_. I bought A-Data SDHC 16GB Card, but whitout tweaking it won´t be recognized.

So, please, can someone suggest me which SDHC 8-32 GB are working out of the box (so, after standby no nautilus pop up windows, freezing and other issues...):popcorn:

---

