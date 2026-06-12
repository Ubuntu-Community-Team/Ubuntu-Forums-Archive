---
title: "Summertime change causes rsync backup problem"
date: 2009-05-06
forum: General Help
---

### Post by MarkRennie on 2009-05-06
Hi there.

I use ubuntu 8.04LTS to manage my photo collection on an ex-windows pc. I use grsync to back up photos from the internal NFTS drive to an external USB FAT32 drive, with the options "preserve time" and "windows compatibility" set. Normally it works fine, but after the wintertime-summertime time-change it insists on backing up all the photos, which takes forever.

Listing the drives after the time change, I see the source (NFTS) drive gives a "date modified" time for each photo that is one hour different (later) than that shown for the same photo previously stored on the destination (FAT32) drive, eg 12:40:00 CET vs 11:40:00 CET. I imagine this it what´s causing the problem, but how do I fix it?

I have already filed this question as a "bug" for grsync, but as I don´t really know if it´s related to grsync or not I´m filing it again here. I´d be grateful for any suggestions, work-arounds, or a pointer in the right direction, and sorry for duplicating the question.

Regards,

Mark Rennie

---

### Post by dandnsmith on 2009-05-06
It looks as if it's a by-blow of a feature which I've seen adverse comments about.
I've noticed that Ubuntu has had problems with the time, even after the correct locale has been set, and someone posted that it was due to the method of keeping the time organised. I've seen fights over what the PC clock should be set to between summer and winter time changeovers, and recently while experimenting found that 8.10 gave problems keeping the correct time displayed between reboots, whereas 9.04 doesn't.

I've absolutely no idea about workarounds, especially if you're talking about NTFS filesystems (but are they maintained by Windows?, and do the pix get added by Windows?)

---

### Post by MarkRennie on 2009-05-26
No, there´s no windows anymore, the pics are added and maintained by ubuntu on the internal NFTS drive then backed-up to the USB FAT32 drive using grsync. Grateful for any ideas. Mark

---

### Post by CatKiller on 2009-05-26
Maybe using UTC for the hardware clock would help. That is why it's the default on most Operating Systems; so that the time is strictly increasing.

```
gksudo gedit /etc/default/rcS
```Set 

```
UTC=yes
```

---

### Post by MarkRennie on 2009-08-28
Hi there.

Sorry not to get back to you but I was away. I tried what you suggested CatKiller but it didn´t seem to make any difference.

In the end I´ve solved it for the photos by using the ignore-existing option, as I rarely edit photos and when I do I give them a new filename. My work stuff and files I actually change frequently are under a different directory tree, and it doesn´t take too long to copy all that over on the once-a-year occasion that this problem crops up.

Thanks both for your help. And CatKiller, your name, is there a story there?...

Cheers,

Mark

---

### Post by CatKiller on 2009-08-28
> **MarkRennie said:**
> And CatKiller, your name, is there a story there?...

Not really. It's just my name. I quite like cats, actually.

---

