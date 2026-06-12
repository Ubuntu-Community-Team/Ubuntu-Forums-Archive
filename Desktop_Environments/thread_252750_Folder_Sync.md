---
title: "Folder Sync"
date: 2006-09-07
forum: Desktop Environments
---

### Post by b1g4L on 2006-09-07
I have two separate directories with music files in them (mp3's mostly). I always put my new music in only one of those directories. I would like to be able to "update" the other directory with just the new files. Is there a Linux command or script that can do this "update" of only the new files that have been added?

---

### Post by etank on 2006-09-07
Check out Unison ([http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)) it will work on a local machine or across the network and its cross platform if you need that.

---

### Post by mmcmonster on 2006-09-07
Take a look at rsync.  I asked [a similar question]("http://www.ubuntuforums.org/showpost.php?p=1447032&postcount=10") a couple weeks ago and have fallen in love with rsync since then.  I put the rsync command in a small script and run it as needed.  Others would have it run automatically on a periodic basis if you are sure that both the source and destination directories are always available/mounted.

---

### Post by b1g4L on 2006-09-07
Thanks guys! I'm checking out both options and seeing which works best for what I need. I appreciate your help and quick response.

---

