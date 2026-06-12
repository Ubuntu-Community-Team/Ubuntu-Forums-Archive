---
title: "NTFS, Asian characters not recognized"
date: 2005-03-16
forum: Desktop Environments
---

### Post by canglan on 2005-03-16
Hi folks,

I recently followed the instructions on [http://www.ubuntuguide.org/#mountunmountntfs](http://www.ubuntuguide.org/#mountunmountntfs) , have the NTFS partition mounted successfully. However, one thing is that, all of the files which have Chinese filenames are unrecognized (can not see them in Linux).

Is it possible to fix it? Thanks.

Regards,
Canglan

---

### Post by canglan on 2005-03-16
Anyone? :/

---

### Post by kahping on 2005-03-16
it's not just Asian characters that have this problem. i have some files and folders on my NTFS partition that contain "Ä" in them and Ubuntu just displays them as this squarish thingy  :-( 

i think it probably affects all characters that are not part of the standard alphabet(as in ABC123abc...). 

can anybody at least explain y this happens? i'd really like to know...

kahping

---

### Post by Miguel on 2005-03-17
I'd bet it has something to do with font encoding. I've had some issues as well when viewing, let's say, UTF-8 files under ISO 8859-1 (or viceversa). I have noticed this because there are a couple of nonstandard characters in spanish.

So the problem could be that the windows font encoding is different that the Ubuntu encoding (iso-whatever or utf-8).

Hope it helps

---

### Post by kahping on 2005-03-17
thought so...

darn M$, why can't they follow standards properly? :-P

kahping

---

### Post by Julius on 2005-03-17
Same happends to me with some spanish characters... it's quite annoying :(

---

### Post by canglan on 2005-03-18
Sorry for bumping the thread, I hope someone with a solution will drop in. ;)

---

