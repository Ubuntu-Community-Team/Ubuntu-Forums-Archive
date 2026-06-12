---
title: "Ubuntu, Vista &amp; shared partitions..."
date: 2009-06-10
forum: General Help
---

### Post by Gizenshya on 2009-06-10
I have a dual-boot system (Ubuntu and Vista Ultimate x64).  Both are installed on my C drive, and D drive is a large storage drive.  Ubuntu was installed form a Live CD within windows (so one partition on each drive).

My problem (symptoms) and what I've tried are exactly the same as in the below link, with the same results.  All sources I've been able to find thus far have had the same endpoint (given up, and resorted to backup and format).  This is the most succinct and representitive thread I've come across.

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/1023843.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1023843.html)

So I figured I'd try here to see if the Ubuntu gurus had any ideas :(

And yeah, Ubuntu interacts with the drive like normal.  Smart status is very good (98%), as it is only a couple months old and is in sleep mode 95% of the time.

---

### Post by Megrimn on 2009-06-11
Does Windows recognize the D drive at all then?  If yes, then what format does it say the drive is? RAW, NTFS?

[EDIT] If you can see the D drive from windows, here is what I would do:

1. back up any thing you want to keep from drive D. You'll probably have to do this through ubuntu.

2. boot windows

3. go into "(my)computer" where all your drives are displayed (C, D, usb drives, sd cards, etc.) 

4. Right click drive D

5. select "Format..." from the menu

6. In the window that pops up, make sure that the disk is going to be formatted in NTFS.  In fact, hitting the "Default" button should give you what you need.

7. click "Start".

8. Take a break and get some work done. This may take a while.

9. When done formatting, Windows should be able to utilize it again.  

10. Put your stuff back on drive D.  


the funny thing is, I had a similar problem, but it was with a floppy disk working between Win95 and Win98.  95 could write to a disk in RAW format, but 98 couldn't.  had to back-up the files on the 95 machine, then format it to FAT32 with 98.  *THEN* I was able to use it...

---

### Post by Gizenshya on 2009-06-12
well, I could do that.. but I don't want to format.  Vista does recognize it, and yes, it sees it as RAW.  The hard drive is 1 TB, and it's full.  That alone would take hours to backup.. but effectively days because I'd have to buy and ship another drive to which to backup the data first.  And then formatting it would take more hours... (I do full formats because I don't want any surprises of dead sectors).

Lots of work... especially because there isn't anything really wrong with it (since Lunix uses it and recognizes it fine).  Seems to be an OS issue, and independent of the drive... unless maybe it is a software issue on the drive? (logs or something).

any other remedy?  or any idea of the reason for Vista's not reading it correctly?

---

