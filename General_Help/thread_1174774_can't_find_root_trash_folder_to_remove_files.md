---
title: "can't find root trash folder to remove files"
date: 2009-05-31
forum: General Help
---

### Post by oponto on 2009-05-31
hi.

IN INTREPID:
All files I directly deleted or move to trash and deleted moved to /root/.local/share/Trash          . If I applied the nautilus "Delete" (right click > "Delete"), the file finally left.

IN JAUNTY:
However, I made a fresh install of jaunty and now I cannot access this directory anymore; still using "gksudo nautilus". So if I have to delete too much, my disk will be full of this strange files which strangely still exist in any strange root folder I strangely cannot find anymore.

How do I know those files are still using space anywhere? 
>>>>>>>The Disk Usage Analyzer says so: The graphic looks good^ but the "Free Space" shows that I cannot free some space by deleting files !


uhm ::D

---

### Post by jonathanysp on 2009-05-31
Where does the disk usage analyzer show the files to be? have you tried using the command line to delete them? sudo rm (-f -r) /path/to/files     add the -f to force remove it and -r to delete folders, but be careful not to remove any important files.

---

### Post by oponto on 2009-05-31
yo :)


The disk usage analyzer does not show the files anyway, not even the bar charts (did not mention that properly before).

Only the upper line "Free Space" (Used Space) gives the important clue that there is no more space after emptying trash.

In future I will only delete by command line, I hope that would finally delete any files (Cant try yet because big file operation running).

but one problem remains, I cannot try to delete the strange files who strangely use space   by command line, because I can't even find them (Disk Usage Analyzier does not show them in its graph/charts, it only shows that there is not more free space after deleting big files by trash or <rightclick->nautilus->delete.

Google says^^ jaunty has still same root trash location, heck.

---

### Post by jonathanysp on 2009-05-31
mm you can try using filelight which is similar to disc usage analyzer maybe that will work. Im not sure but maybe theres a command in the terminal that can search for big files in a directory?

---

### Post by oponto on 2009-05-31
gonna try this,

but


where is the root Trash directory ?! (9.04)

---

### Post by Legace on 2009-05-31
> **oponto said:**
> where is the root Trash directory ?! (9.04)

/root/.local/share/Trash/files

---

### Post by oponto on 2009-05-31
damn it no way !

___________________________________________
command:```
gksudo nautilus
```
nautilus:```
/root/.local/share/Trash/files
```
output: ```
Could not find "/root/.local/share/Trash/files. Please check the *******^^ spelling and try again
```
_____________________________________________
command: ```
gksudo nautlius /root/.local/share/Trash/files
```
the same
____________________________________________
tried it with  only /root/.local
no way
___________________________________________
.local and further does not exist -.-



heck?!

---

### Post by edu1962 on 2009-06-03
___________________________________________
command:```
gksudo nautilus
```

and then as in png.

That's how it works for me in 8.04 LTS.

---

### Post by dcstar on 2009-06-03
> **oponto said:**
> 
.........
.local and further does not exist -.-


I doubt that that tree will exist until a logon to the root account is done.

---

### Post by mhgsys on 2009-06-03
navigate to ```
/home/USERNAME/.local/share/Trash/files
``` as root.

---

### Post by oponto on 2009-06-04
> **edu1962 said:**
> ___________________________________________
command:```
gksudo nautilus
```

and then as in png.

That's how it works for me in 8.04 LTS.


ok "open in new tab" results in the following (ran nautilus with gksudo..).

---

### Post by mcduck on 2009-06-04
> **oponto said:**
> ok "open in new tab" results in the following (ran nautilus with gksudo..).

You'll find root's trash in /root/.local/share/Trash. For some reason the Trash shortcut in the places-panel doesn't work for root.

If that directory doesn't exist, you have no files in root's trash.

edit: Nice tip, shift+delete removes files immediately instead of moving them to trash. Useful when deleting files as root as you won't have to empty root's trash afterwards.

---

### Post by WIREHEAD on 2009-06-08
Shift + Delete - Thank you !

No trash to empty.

---

### Post by craig0927 on 2010-07-09
I was having a problem in Karmic with some sbackup files I deleted with gksudo nautilus, and there was no /root/.local/share/Trash folder.  I ended up finding the files in /home/Trash-0.   Does that make sense to anyone?

---

### Post by michaelcochez on 2011-03-05
> **craig0927 said:**
> I ended up finding the files in /home/Trash-0.   Does that make sense to anyone?
I can't tell whether it makes sense, I can only confirm that it is the location where I found the files as well. (Ubuntu 10.10)

---

