---
title: "how to change directory to Filesystem ?"
date: 2009-06-01
forum: Desktop Environments
---

### Post by tonjaa on 2009-06-01
i try to change directory in terminal to Filesystem and drive 3 , drive 4 ( second drive )
but i can't i want to know to correct way .where 's the first directory that i must to go?
from 
[COLOR=DarkOrange]tonjaa@tonjaa-desktop:~$ [/COLOR]
please tell me by step.

---

### Post by Aubergines on 2009-06-02
Can you re-phrase this to make it more clear. I don't understand what you want to do. I think you're also a bit confused on what a filesystem is

---

### Post by mcduck on 2009-06-02
If you want to go to same place that the File Manager calls "File System", "**cd /**" will do the trick (moving you to root level of the file system hierarchy).

I didn't really understand the part about "drive 3 , drive 4 ( second drive )".

---

### Post by tonjaa on 2009-06-02
i sorry if i write wrong i new for Linux. 
i try to change directory to  File System but i don't know the root of Filesystem.
when i go > Places>Computer - File Browser box   i saw icon of cdrom , (hd0,3),(hd0,4),media drive (old hd) ,Filesystem
that i saw Filesystem but when i use command cd to Filesystem i can't. i don't know root .i try to chenge directory to media but it's can't saw Filesystem i saw cdrom and (hd,..). like this
[COLOR=DarkOrange]
tonjaa@tonjaa-desktop:~$[/COLOR] cd /media
tonjaa@tonjaa-desktop:/media$ ls
cdrom  cdrom0  TON3  TON4  TORTON009
[COLOR=DarkOrange]tonjaa@tonjaa-desktop:/media$[/COLOR] ls -a
.  ..  cdrom  cdrom0  .hal-mtab  .hal-mtab-lock  TON3  TON4  TORTON009
[COLOR=DarkOrange]tonjaa@tonjaa-desktop:/media$ [/COLOR]

that i want to know how to chenge directory to[COLOR=DarkOrange] Filesystem[/COLOR]. 
where the [COLOR=SeaGreen]root[/COLOR] that correct ?

---

### Post by MichaelSammels on 2009-06-02
OK. Open Terminal. Once there type this:

```
cd ../../
ls
```

This is your Filesystem. :)

---

### Post by tonjaa on 2009-06-02
[COLOR=Black]ok. now i understand i don't to type  [/COLOR][COLOR=DarkOrange]File System[/COLOR] 
 i saw in File System has - bin , boot ,cdrom,dev,etc,home,lib,media,mnt,usr,sys....and more
if i want to cd to that directory i can use command [COLOR=Green]cd /....name of directory [/COLOR]
don't type[COLOR=DarkOrange] File System[/COLOR] .
[COLOR=DarkRed]thank you for everybody [/COLOR]
for human beings.

---

