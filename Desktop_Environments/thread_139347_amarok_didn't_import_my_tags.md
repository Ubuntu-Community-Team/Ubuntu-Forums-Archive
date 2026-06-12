---
title: "amarok didn't import my tags"
date: 2006-03-03
forum: Desktop Environments
---

### Post by auburn on 2006-03-03
Anybody else import mp3's from itunes and not been able to import the tags too? I'm suspicious it's entirely to do with my network configuration. I set up a cifs share in my fstab to my roommate's winxp machine. I scanned the itunes folder containing the mp3s and all the songs were added to my sqlite database, in amarok, but the artist, album, etc, fields were never filled. Only the song name is filled and it's the filename (eg "01 Amazing Grace"). 

Here's what my fstab entry looks like.
//192.168.123.100/itunes        /mnt/mere3dith-itunes cifs username=username,password=password 0 0

Oh, and I had my roommate make her network share, read-only.

I built and installed amarok from svn according to this howto:
[http://ubuntuforums.org/showthread.php?t=80492&](http://ubuntuforums.org/showthread.php?t=80492&)

---

### Post by testube_babies on 2006-03-04
i had a similar problem with my itunes-to-amarok conversion.  apparently, itunes saves all song data in a seperate xml file, and doesn't always write an ID3 tag to music files.

anyway, to fix the problem i went into itunes and selected my entire library, right-clicked and chose "convert id3 tags."  choose id3 v2.3 (2.4 for some reason isn't always compatible).  this should write new tags for all of your songs and hopefully solve your problem!

---

### Post by auburn on 2006-03-04
oh, good. that sounds reasonable (and simple). we'll try with a test batch when my roommate returns monday.

I'll reply again at the beginning of next week.

thx!

---

