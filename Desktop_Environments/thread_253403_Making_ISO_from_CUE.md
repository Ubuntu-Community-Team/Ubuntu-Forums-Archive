---
title: "Making ISO from CUE?"
date: 2006-09-08
forum: Desktop Environments
---

### Post by allanlewis on 2006-09-08
Hi,

I have a CUE file and two IMG files. (The CUE file describes the two IMG files.)

How do I make an ISO from this? GnomeBaker is happy to burn the CUE file but only to a CD, i.e. the app doesn't include an "image recorder" a la Nero.

---

### Post by glotz on 2006-09-08
First you search the forum before asking silly questions! [http://www.ubuntuforums.org/showthread.php?t=239407&highlight=iso+cue](http://www.ubuntuforums.org/showthread.php?t=239407&highlight=iso+cue)

(maybe you didn't know it's silly...)

---

### Post by allanlewis on 2006-09-08
I always search the forums first!

I found that thread you linked to and it's not what I want. I downloaded bchunk and it doesn't do what I want because it requires bin files and not img files. All it did was make 2 "ugh" files and I don't know what to do with them. In any case my cue file refers to 2 img files and bchunk only deals with one.

I've tried img2iso (originally isodump from [http://linux.xulin.de/c/](http://linux.xulin.de/c/) ) but that only works with one of my img files.

Any other ideas?

---

### Post by glotz on 2006-09-08
First, sorry for being rude. Too little sleep I guess...

Looks like it's shots in the dark time... Are you positively sure you're not missing a cue file? Or maybe you could merge the 2 imgs to one?

---

### Post by allanlewis on 2006-09-08
Well, the cue file is of the following format...
```
FILE "file1.img" BINARY
TRACK 01 MODE1/2048
INDEX 01 00:00:00
POSTGAP 00:02:00
FILE "file2.img" BINARY
TRACK 02 MODE1/2048
INDEX 01 00:00:00
POSTGAP 00:02:00
```
...where my two img files are file1 and file2.

---

### Post by glotz on 2006-09-08
How about then making 2 cue files of it?

---

### Post by allanlewis on 2006-09-09
#1: I don't know how to make cue files.

#2: These files are part of a package I downloaded but it only came with instructions on how to make a CD with it (which I can do easily) but not on how to make an ISO image so I could use it with a virtual machine (i.e. vmware) which is what I want to do (without burning a real disc).

---

### Post by glotz on 2006-09-09
The .[cue](http://en.wikipedia.org/wiki/Disk_image#.BIN.2F.CUE)'s just a plaintext file, just right click > create an empty file and paste the content in and rename to whatever.cue. Then hit them with bchunk.

---

### Post by altonbr on 2008-01-05
(Feisty-Hardy)
Use ccd2iso, not img2iso
> $ sudo aptitude install ccd2iso
$ ccd2iso $img_file $iso_file

---

