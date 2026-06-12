---
title: "Problems using live CD to rescue bad drive"
date: 2009-04-30
forum: General Help
---

### Post by Old *ix Geek on 2009-04-30
PLEASE NOTE: I had brain surgery to remove a tumor 3 weeks ago and am having a REALLY BAD time right now physically. I can't focus my eyes for more than a few minutes at a time, 2-3 times per day, and to say I have brain fog is just too much of an understatement. I've only been home for a week or so and really feel like crap. I need help here. Please don't tell me to read somewhere else or Google something, etc. My windows of opportunity for reading are VERY limited, so I'd appreciate some help.  Thank you.

Here's the problem: The drive in my laptop decided to crash.  Of all times, it just had to do it now!  I am attempting to use a live CD to rescue files from it.  I was successful ONCE.  All other attempts at booting from the CD yield a long process of checking the drive, reporting I/O errors and failed FSCKs, and the like, followed by a non-GUI boot. I end up at a prompt and have no way to access the hard drive, i.e., the only directories listed are from the CD.  I just need to boot from the CD so I can salvage files. As I said, I did it once successfully but I'm not doing anything differently now--I'm just choosing the "run from CD without changing your system" menu option, but it's not working.  What am I missing?

Also, the ONLY directory left on the drive that I haven't been able to salvage files from is my home directory.  On my one successful boot from the CD I was unable to navigate to it from either a command line or GUI. I don't recall the specific errors, but I think it's basically fried (as in I think it's the most damaged from the drive failure).  Is there anything anyone can think of that I can do to try to rescue its files?

Thanks in advance for any ideas, and sorry for the snotty attitude but I really feel dreadful. :(

---

### Post by dandnsmith on 2009-04-30
1. It's possible that more than the drive is damaged or not working properly. RAM seems to be a prime candidate, but a failing CD drive must also be a candidate (with that worked once, and now fails to boot). I'd try memtest if that is one of the boot options.

2. do you know what the basic filesystem type was - ext2, ext3 etc, as this affects the possibilities of recovery.

3. Is it possible to try another recovery system, via a download and burned CD - [System Rescue CD](http://www.sysresccd.org/Main_Page) comes to mind (but this carries its own reading burden)?

4. Is it possible to boot from USB - just to give another avenue for trials?

---

### Post by Old *ix Geek on 2009-04-30
Thanks, Derek.  The CD is booting as I'm ending up with its filesystem as the only one listed.  It's just not booting in a useful/usable way. :(

The drive is ext3.

---

### Post by dandnsmith on 2009-05-02
If you cannot see anything on the HDD, then that strongly suggests a failure.

There have been reports of success with what seems to me a rather drastic 'solution'. You extract the HDD, wrap it in something which will keep out any water/water vapour, stick it in a fridge for a while, take it out and connect it and boot from the CD immediately - sometimes this will get it working long enough to extract files (but it cannot be expected to stay working long, and it depends on the failure mode).

---

### Post by Monsieur Gonzalez on 2009-05-02
You might give [SystemREscueCd]("http://downloads.sourceforge.net/systemrescuecd/systemrescuecd-x86-1.1.7.iso") a try. It's a bootable linux-based CD with lots of well, system rescue apps, like :

"TestDisk[4]
    Recovers lost partitions, deleted files and fixes partition tables and boot sectors. It supports reiserfs, ntfs, fat32, ext2/3 and many others"

---

### Post by dandnsmith on 2009-05-02
I thought of that one first off, re-read the OP, refreshed my memories of the System Rescue CD, decided that it would be a concentrated learning experience, and then didn't recommend it.

Anyway, the trick is to get the HDD even recognised as readable.

---

