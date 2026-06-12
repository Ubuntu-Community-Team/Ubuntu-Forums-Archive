---
title: "Best File system for mp3's and pictures?"
date: 2009-06-20
forum: General Help
---

### Post by rsmseys on 2009-06-20
I am trying to get a separate home drive set up so that I can access all my files from the separate drive on Ubuntu. The majority of my files are mp3's and jpg's, so I was wondering what would be the better alternative from ext3. I tried formatting the drive (after backup of course) to ext3, but immediately 50GB was spent on god knows what. So it seems really inefficient. Any recommendations?

---

### Post by Soul-Sing on 2009-06-20
How,and with which program did you format the disk/partition in ext-3?

---

### Post by rsmseys on 2009-06-20
> **leoquant said:**
> How,and with which program did you format the disk/partition in ext-3?

GParted GUI in Ubuntu 9.04

---

### Post by starcraft.man on 2009-06-20
> **rsmseys said:**
> GParted GUI in Ubuntu 9.04

Whaaaaa? I think you did something seriously wrong. I mean really wrong, go to gparted site and look over the documentation tuts if your unsure. I've been using gparted for years and I've never had such a large amount of space used after formatting. At most a few mb of waste, try again.

---

### Post by t0p on 2009-06-20
I suggest you use ext3.  What you said about 50 gigs being taken up directly after formatting sounds most odd.  Believe me, ext3 is *not* inefficient, otherwise it wouldn't be the default format of a great many Linux distros.  Please navigate to this drive and run the command

```
ls -al
```

so we can see what has taken up 50 gigs.

---

### Post by rsmseys on 2009-06-20
I simply deleted the NTFS filesystem that was present on the drive, and right-clicked, hit "New" and selected ext3. Then Apply.

---

### Post by rsmseys on 2009-06-20
> **t0p said:**
> I suggest you use ext3.  What you said about 50 gigs being taken up directly after formatting sounds most odd.  Believe me, ext3 is *not* inefficient, otherwise it wouldn't be the default format of a great many Linux distros.  Please navigate to this drive and run the command

```
ls -al
```

so we can see what has taken up 50 gigs.

I deleted the partition, but I'll try and replicate it by creating it again, and then posting the results of the command. Stand by. :)

Edit: PS. Creating it again is taking FOREVER!

---

### Post by rsmseys on 2009-06-20
Side note: I read an article, and looked at some benchmarks of the XFS filesystem, and I was wondering if Ubuntu supports it fully?

---

### Post by rsmseys on 2009-06-20
Here's a screenshot of what I see. I ran the command 

```
ls -al
```and the results are shown in the picture as well.

I'm very confused. :-k

[URL="http://img413.imageshack.us/i/screenshotkbc.png/"][IMG]http://img413.imageshack.us/i/screenshotkbc.png/%5D%5Bimg=http://img413.imageshack.us/img413/1373/screenshotkbc.png[/IMG][IMG]http://img413.imageshack.us/img413/1373/screenshotkbc.png[/IMG]
[/URL]

---

