---
title: "which filesystem for external disk?"
date: 2009-06-08
forum: General Help
---

### Post by barna on 2009-06-08
Hi,
I am wondering what is the best filesystem for a 320 GB external USB disk, which I mainly want to use to store my pictures, and bring it to make presentations. If I want to avoid carrying my superheavy notebook, I can rely on computers on-site, which will most probably run windows only.

- fat 
advantage: linux + windows can read it. drawback: ?

- ntfs
advantage: linux + windows can read it. is it more stable than fat? any advantage over fat? as far as I know it has read/write/etc permission bits, and also user IDs. If I set everything read-writeable, the different user-ID (different from the actual user reading it) should make no difficulty. is it correct?

- ext3 or any other linux fs: journaling (not a too big advantage, though, since I will not heavily write this filesystem). drawback: works only with linux.

concerning this last issue: is there a way to also put a live linux system on this disk, so that I can bring my favourite linux environment along with me, and don't need to use windows' picture and fax viewer, which I hate?
- can today's computers boot from an external usb disk, so that I could copy some linux system and a bootloader onto this disk?
- do you know about any other 'mobile' linux system? who has experience with wubi, for example? 

thanks

---

### Post by SuperSonic4 on 2009-06-08
fat's disadvantage is not being able to copy files bigger than 4GiB:

I would go with ntfs. I've not had any problems with ntfs although it's not as good as ext* it is a necessary evil for windows compatibilty. If you defrag it every so often you ought to be ok. 

I'm pretty sure today's computers can boot from USB, mine certainly can but the older PCs used by companies may not - they may also password protect the BIOS. If you can manage it be aware that they may be ignorant as to linux and think you're 'hacking'

If you wanted you could always partition the drive, have one with ext4 and linux on and the other with ntfs for data on.

For external disks you can use gparted as you would with any other hard disk - they act in the same way

---

### Post by Jaded Misanthrope on 2009-06-08
As far as I am aware, NTFS is the generally-used filesystem for portable drives unless you're sure that the Windows computers you'll be using it on have an application to read ext3 (there's a pretty good one somewhere that I use if I dual-boot, but I can't remember what it is called for the life of me) in which case you could use ext3 instead.

I've not seen anyone running FAT32 in years; didn't NTFS supersede FAT anyway?

---

### Post by Therion on 2009-06-08
NTFS.  Seriously.

---

### Post by davidmohammed on 2009-06-08
I would use ext3 for your external harddrive 

Install on windows the freeware described in the following useful link
[URL="http://tombuntu.com/index.php/2007/08/14/ext3-file-systems-in-windows/"]
http://tombuntu.com/index.php/2007/08/14/ext3-file-systems-in-windows/[/URL]

---

### Post by Lampi on 2009-06-08
fat is like  the least reliable filesystem, but also the most widespread if it comes to external media - think of what filesystems your usb sticks were shipped with, think what filesystem your external drive was shipped with, I bet it was fat, wasn't it? It runs just perfect on both windows and linux. I see *no* drawback if you know how to handle fat. But I admit it is tricky! There is no error correction - so if you corrupt your filesystem badly you are doomed and you will loose badly corrupted data.

ext3 would be best choice if you think about stability - it's poor support on windows is a huge drawback.

which leaves ntfs... support on linux has *much* improved - you absolutely can give it a try.

Nevertheless my choice would be fat. I'd split the drive into small partitions.

---

### Post by barna on 2009-06-08
Hi, thanks for the many responses. I seem to favour ntfs.
Yes, my external drive was preformatted with fat. Partitioning it with different filesystems doesn't seem to make too much sense for me (why should I write some of my pics onto ntfs, some of them onto ext3?)
So I will go for ntfs.

(I have another external hard disk, which I use to backup my home directory on my notebook, and store other data - this hard disk has obviously ext3)

Thanks

---

### Post by Lampi on 2009-06-08
> **barna said:**
> Partitioning it with different filesystems doesn't seem to make too much sense for me (why should I write some of my pics onto ntfs, some of them onto ext3?)
You got me wrong there, I'd split a fat formated drive into small fat partitions. Like this it is easier to handle if errors should occur.

> **barna said:**
> 
So I will go for ntfs.
Good choice as well, probably best if you don't feel safe handling fat.

---

