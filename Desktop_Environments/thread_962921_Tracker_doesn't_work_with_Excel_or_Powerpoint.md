---
title: "Tracker doesn't work with Excel or Powerpoint"
date: 2008-10-29
forum: Desktop Environments
---

### Post by HDave on 2008-10-29
I have a ton of excel and powerpoint files, but it appears that Tracker isn't scanning this inside of them for content to search on.  I do my editing in openoffice, but I use the MS file formats to be compatible with co-workers and business partners.  

Anyone else experience this?  Is there a fix?

---

### Post by ad_267 on 2008-10-29
Looks like other people have the same problem: [http://ubuntuforums.org/showthread.php?t=673206](http://ubuntuforums.org/showthread.php?t=673206)

Installing the wv package might help but it looks like it may only work with .doc files.

---

### Post by HDave on 2008-10-30
I believe you are correct.  How dissapointing.  

I have read that Beagle works with excel and powerpoint.  However, I indexed my filesystem with that last night and it doesn't scan them either!

At this point, I am contemplating moving on to Google Desktop for Linux, which I am trying right now.

---

### Post by HDave on 2008-11-09
After reading the Google desktop documentation, I found out that wv will allow tracker (and Beagle and Google Desktop) to index .doc files in MS format...and that gnumeric allows for the index of .xls files.

So at this point, Tracker, Beagle, and Google desktop are all tied as far as indexing content goes with one big exception.  Google desktop indexes the emails in my outlook archive files (way cool).

Anyone have a clue as to how to get these things to index powerpoint files?

---

### Post by HDave on 2008-11-21
I have since discovered that "catdoc", available in the repos, contains a program called "catppt" which extracts the text from powerpoint files.  Now if I could only get tracker to use it....

---

