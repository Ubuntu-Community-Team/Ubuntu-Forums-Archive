---
title: "Unison Help"
date: 2008-10-16
forum: Desktop Environments
---

### Post by Quarkrad on 2008-10-16
Is there a specific forum or somebody I can talk to re Unison?  I am a newbie and have some basic questions (e.g. command line txt to kick something off).  I have searched around but there does not seem to be anything.  Thanks.

---

### Post by Mazin on 2008-10-16
First check their documentation:
[http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html](http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html)

I don't think Unison is actively developed anymore, but the mailing list is probably still active.
[http://www.cis.upenn.edu/~bcpierce/unison/lists.html](http://www.cis.upenn.edu/~bcpierce/unison/lists.html)

---

### Post by Quarkrad on 2008-10-17
Mazin - many thanks.  out of interest - if Unison is no longer being developed what app does Ubuntu people use for simple folder sync'ing on a local machine.  All I want to do is to sync' user daa folders on one hd to another hd on my pc.

---

### Post by vanadium on 2008-10-17
There is probably still a yahoo user group. I have followed that some years ago.

Anyway, there is a difference between "synchronising" and "mirroring". If you just want to make one destination directory the same as a source directory, then you are "mirroring". rsync will do a perfect and fast job:

rsync -av --delete <source> <destination>

True "synchronising" is where you want to make two directories similar that have been edited each one independently. Some files were updated in the source, others were updated in the destination (typical scenario for the somewhat less disciplined user working on two different computers).

There unison fills a unique gap: I know of no other program that can do that. It is capable of determining which of the two directory trees contains the most up to date version, and will for each file copy the updated version to the version that was not updated. If a file was deleted in one directory tree, and was not changed in the other, it will be deleted in the other directory as well. If a file was deleted in one directory tree, but was updated in the other, it will be copied. There is one case in which unison can not know: since the last run, you updated the same file at different times in both directories. then unison will ask which of the two versions you want to keep.

Bottom line: if you see for your self that you just want to "mirror", rsync will probably be easier.

---

### Post by treesurf on 2008-10-17
There is also a graphical version of unison: unison-gtk.  Easy for us command line dummies.

---

