---
title: "How do I..."
date: 2006-01-15
forum: Desktop Environments
---

### Post by DarkDancer on 2006-01-15
Sorry, I searched but could not find it and as of yet, the Wiki makes little sense to me. How do I copy a folder from a ntfs drive to a ext3 drive, I tried this:
cp /media/hda1/"Drive D"/mp3z /media/hdb1/

and it returned with this:
cp: omitting directory `/media/hda1/Drive D/mp3z'

are there simple easy instructions?

---

### Post by RAOF on 2006-01-15
Do the same thing, but using the "-r" (or "-R", or "--recursive" - they're all the same) option.

So it would be:
```
cp -R /media/hda1/"Drive D"/mp3z /media/hdb1/
```
And in general, if you are not quite sure how to get a command to do something, you can try "man <command>".  That gives a brief manual of the options that the command takes, and what they do.

Alternatively, you could do it graphically in nautilus.  Just drag'n'drop, like in windows/OS:X/any modern GUI system.

---

### Post by Wolki on 2006-01-15
[QUOTE=DarkDancer]cp /media/hda1/"Drive D"/mp3z /media/hdb1/[/QUOTE]

You need to copy recursively. Do it like this:

cp -r <source> <destination>

Alternatively, you could use the graphical file manager of your choice. :)

---

### Post by DarkDancer on 2006-01-15
I tried the graphical file manager, it won't let me see the contents of the ntfs drive....

---

### Post by DarkDancer on 2006-01-15
Thanks Raof, I think that tha tworked... ;)

---

