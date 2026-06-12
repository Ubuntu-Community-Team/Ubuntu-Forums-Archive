---
title: "UNtar with alternative for CPIO"
date: 2009-05-15
forum: General Help
---

### Post by StrangeWill on 2009-05-15
This is a continuation of my corrupted tar thread, I was able to get a 198GB recovery file... with TAR I get an error on a .vob, that's fine, I'll get the DVD again.

However....

Currently using "tar -xvf storage.tar" results in:
tar: Skipping to next header
tar: Error exit delayed from previous errors

On the .vob file.


If I use CPIO...
"cpio -F storage.tar -i -v"

I can get files after it, sweet... Oh wait, CPIO doesn't have @LongLink support, so I lose any files with long file names as they are all extracted into eachother.

So I need to either patch CPIO to support @LongLink, or get another tar extraction utility that will continue after a failed file like CPIO will, AND support @LongLink.


That or to tell tar to extract everything but .vob files.

---

### Post by StrangeWill on 2009-05-15
PowerArchiver will only extract to the broken file. 7-Zip wont even open the damn file. >=(

---

### Post by StrangeWill on 2009-05-15
IZarc has the same problem as CPIO + TAR, only shows some files AND can't deal with long filenames.

CPIO was able to get to music directories that no other applications could read into...

---

### Post by StrangeWill on 2009-05-15
Nevermind, I ended up tweaking an old CPIO patch to work on the new CPIO, compiled it and it's working, yay. :D

---

