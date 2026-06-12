---
title: "I want to rename many files"
date: 2009-04-23
forum: General Help
---

### Post by seepage87 on 2009-04-23
I'd like to batch rename all my TV shows and movies to be [Boxee compliant]("http://forum.boxee.tv/showthread.php?t=1147").  They're stored on my server, and ideally I'd like a good program that can be used in the CLI so I can do it at work via SSH.  A GUI program is fine too, even a windows one I suppose.  Most important is that it will do most of the work for me. I typically have my TV shows categorized into folders by season, and the episode numbers are usually in the file name.  If it could pick up on this information to accelerate the process, that'd be great.  If it will add the meta-data to the video files for me, even better.  Any suggestions?  Thanks.

---

### Post by whollycow on 2009-04-23
What kind of renaming do you need to do?  Are you just changing the file extension?  Converting the names to all caps?  Changing each file to a unique name based on a pattern?  Depending on the extent of renaming, your solution might be short or more involved.

---

### Post by lukjad on 2009-04-23
If I am not mistaken, there is a program called "Bulk Rename" that can be found in Applications->Accessories->Bulk Rename.

---

### Post by whollycow on 2009-04-23
> **lukjad007 said:**
> If I am not mistaken, there is a program called "Bulk Rename" that can be found in Applications->Accessories->Bulk Rename.

I have that as well.  I think it's included with the Thunar file manager so it may have to be installed from Synaptic.  

Bulk rename is a good graphic utility but for command line solutions there are millions of different ways to do a rename.

---

### Post by seepage87 on 2009-04-23
I'm mostly going to be changing video files that are in a number of different patters to something like SERIES.S##E##.TITLE.EXTENSION.  How they're currently named depends on the file, but they should have most of that in the file name.  I have several hundred tv episodes at least, so the more work it can save me, the better.

---

### Post by michy99 on 2009-04-23
Have a look at mrename. Description from Synaptic:

A tool for easy and automatic renaming of many files
Mass Rename is a simple pair of shell scripts which make it easier to
move, rename, or copy multiple files at once. It is intended mainly as an
automatic and simple way to rename multiple files with a customizable
prefix and a progressive number. It is also possible to modify the rename
format simply by editing one of the scripts. It is easy, complete, and
efficient, and was written only in sh code.

 Homepage: [http://alfalinux.sourceforge.net/mrename.php3](http://alfalinux.sourceforge.net/mrename.php3)

---

### Post by seepage87 on 2009-04-23
Tried out mrename, I don't think it's going to do the trick.  I tried it and it isn't renaming the files in order (not to mention I can't fine tune certain things). You'd figure it would read the files in by alphabetical order and increment the number each time, but that doesn't seem to be happening.  It's sorta funny actually, this is the output of my test with parts 1-8: 
CS1part2.avi CS3part7.avi CS5part1.avi  CS7part3.avi CS2part6.avi CS4part8.avi CS6part4.avi CS8part5.avi

Anyway, I might just try [MediaRenamer]("http://code.google.com/p/mediarenamer/") from windows; someone mentioned it worked pretty well for the.  Ideally I'd want something like [Musicbrainz]("http://musicbrainz.org/") for video files, including looking up the metadata on some database like thetvdb.  If anyone has something like that, that'd be ideal.

---

### Post by Arndt on 2009-04-23
> **seepage87 said:**
> Tried out mrename, I don't think it's going to do the trick.  I tried it and it isn't renaming the files in order (not to mention I can't fine tune certain things). You'd figure it would read the files in by alphabetical order and increment the number each time, but that doesn't seem to be happening.  It's sorta funny actually, this is the output of my test with parts 1-8: 
CS1part2.avi CS3part7.avi CS5part1.avi  CS7part3.avi CS2part6.avi CS4part8.avi CS6part4.avi CS8part5.avi

Anyway, I might just try [MediaRenamer]("http://code.google.com/p/mediarenamer/") from windows; someone mentioned it worked pretty well for the.  Ideally I'd want something like [Musicbrainz]("http://musicbrainz.org/") for video files, including looking up the metadata on some database like thetvdb.  If anyone has something like that, that'd be ideal.

I like mmv.

---

### Post by MasterZ on 2009-04-23
Hi, 

You can use Gnome-Commander a lightweight file manager. It contains an advanced batch renaming utility whe you can use regex and pattern matching in a simple way.
It's in the repos. 

If you have wine, you can use 'lupas rename' for windows. Very easy, I used it a lot. Just google for it.

---

### Post by doas777 on 2009-04-23
I really like a w32 app called "renamer" for that. it will work fine with wine.
I also found an oss one in the repos called pyRenamer that works almost as nicely.

just a hint, don't try to rename all the files at once. make a series of incremental changes that bring them in line with your expectations. most likely you will never find the magic ruleset that will make all your files consistent with your schema.

good luck,
franklin

---

### Post by labros on 2010-10-01
Hi Did anyone try the Dolphin File Manager? 
You can find it on Ubuntu Software Center 

Open the Folder 
Press Ctrl A (select all)
F2 (rename)
Hit Enter to Confirm 

Example

qwe0001.jpg ew0002.jpg 0zxc03.jpg

Type on the window aa#.jpg or something   

aa1.jpg aa2.jpg aa3.jpg

Works on folders to

Sorry my English is not good :)

---

