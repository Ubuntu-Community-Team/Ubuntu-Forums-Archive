---
title: "File info lost when copying to FAT32 partition"
date: 2006-01-15
forum: General Help
---

### Post by pbb on 2006-01-15
I've noticed when copy files to a FAT32 partition, 
[LIST]
[*]the modification date is set to the current date/time, 
[*]and short filenames (8 characters or less) which are in all-caps are converted to lower case.
[/LIST]

This is probably a general Linux issue, but is there someone who can give me more background information, and possible work-arounds?

---

### Post by dueY on 2006-01-15
Not positive... but check your fstab to see if your FAT32 partition is mounted with utf8?

---

### Post by pbb on 2006-01-15
[QUOTE=dueY]Not positive... but check your fstab to see if your FAT32 partition is mounted with utf8?[/QUOTE]
Yeah, it is. Is this common behaviour, or should the filedate be maintained while copying?

---

### Post by rattking on 2006-01-15
man cp 
says
-p  same as --preserve=mode,ownership,timestamps
that option should preserve your file dates
actually I'm not sure if fat32 is going to give trouble with mode and ownership.. if so 
cp --preserve=timestamps
will do as well

---

### Post by pbb on 2006-01-15
Okay, when I do "cp -p /tmp/file .", I get
```
cp: preserving times for `./file': Operation not permitted
```

But when I do this with sudo, everything goes okay.

I would like all users to be able to preserve timestamps (without using sudo). Does anybody know how I can change the permissions to do this?

---

### Post by pbb on 2006-01-15
Okay, the solution for the filename casing changing, I've found myself: add "shortname=mixed" to the mount parameters in fstab.

The first problem, maintaining date/time for non-root users, stays. I've tried adding "uid=peter" (my username), but that didn't change anything. Any suggestions?

---

