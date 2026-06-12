---
title: "using second drive for storage"
date: 2009-01-28
forum: General Help
---

### Post by jerkemy on 2009-01-28
THis is probably a dumb question, but I'm pretty new to dual booting. I'm running Ubuntu and XP, each in its own partition on my C drive.

I'm wondering what happens if I connect another drive to just use as storage. For instance, can I store mp3s on my E drive, and then have mp3 players in both Ubuntu and XP play them? Or does the E drive need to be formatted one way or the other? Likewise graphics and other media files that are readable by both XP software and Ubuntu applications.


I do a lot of graphics stuff, ultimately what I'd like to be able to do is work online in Ubuntu, save files to my E drive, and then reboot into Windows to work on them with Illustrator and Photoshop etc. (PS I know about InkScape and GIMP but I'm new to them and still learning, so that doesn't really fix my problem.)

thanks!

---

### Post by ww711 on 2009-01-28
> **jerkemy said:**
> THis is probably a dumb question, but I'm pretty new to dual booting. I'm running Ubuntu and XP, each in its own partition on my C drive.

I'm wondering what happens if I connect another drive to just use as storage. For instance, can I store mp3s on my E drive, and then have mp3 players in both Ubuntu and XP play them? Or does the E drive need to be formatted one way or the other? Likewise graphics and other media files that are readable by both XP software and Ubuntu applications.


I do a lot of graphics stuff, ultimately what I'd like to be able to do is work online in Ubuntu, save files to my E drive, and then reboot into Windows to work on them with Illustrator and Photoshop etc. (PS I know about InkScape and GIMP but I'm new to them and still learning, so that doesn't really fix my problem.)

thanks!

If you have an external usb harddive and have multimedia files on that drive, whether you're in Ubuntu or XP, it doesn't really matter. As long as you have applications that can read/access those files.

---

### Post by jerkemy on 2009-01-28
well i want to use a second internal drive actually. Same thing though I assume?

---

### Post by ww711 on 2009-01-28
Yeah, format the secondary drive into a fat32 partition; making it readable in Ubuntu and XP.

---

### Post by indytim on 2009-01-28
Or, as an alternative (which I'm using) format the partition(s) as ext3 and use the Windows app to access the ext3 partitions as shown at
[http://www.fs-driver.org/]("http://www.fs-driver.org/").

IndyTim

---

### Post by Gizenshya on 2009-01-28
ok, what they said... except about the fat32.  There are several advantages to NTFS file system over fat32.  And, Ubuntu now supports read/write to NTFS just as well as it does for fat32.  In fact, I only use NTFS for my drives now that ubuntu supports it readily.  And you also won't need to use an extraprogram for win in order to access it.

---

