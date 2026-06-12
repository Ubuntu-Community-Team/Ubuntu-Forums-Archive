---
title: "Trash bin"
date: 2008-12-15
forum: General Help
---

### Post by davidself1001 on 2008-12-15
I have files in my trash bin that I can't delete (no permission).  So where is the trash bin in the directory hierarchy?

---

### Post by Arup on 2008-12-15
sudo apt-get install trash-cli

sudo empty-trash will then remove any trash with permission problem.

For trash in root use 

sudo su
empty-trash

trash-cli is an excellent method of removing trash in Linux as you hae the chance of recovery in case you deleted some wrong stuff.

---

### Post by adult swim on 2008-12-15
from drs305's disk full tutorial, 
     ~/.local/share/Trash User's Trash (hardy and later)
     ~/.Trash User's Trash (pre-hardy)
     /root/.local/share/Trash System Trash (hardy and later)
     /root/.Trash System Trash (pre-hardy):
     /.local/share/.Trash-1000 NTFS/FAT32/etc: Trash deleted in these partitions is placed in a Trash bin named in accordance with the user deleting the file, e.g. -1000, 1002, -0, etc

and find any trash, run from terminal ```
sudo find / -type d -iname *Trash* | grep Trash
```

---

### Post by cdtech on 2008-12-15
The location is "~/.local/share/Trash/files" just for the record..

---

### Post by davidself1001 on 2008-12-16
> **Arup said:**
> sudo apt-get install trash-cli

sudo empty-trash will then remove any trash with permission problem.

For trash in root use 

sudo su
empty-trash

trash-cli is an excellent method of removing trash in Linux as you hae the chance of recovery in case you deleted some wrong stuff.
I get "Command not found" when I do the sudo empty-trash.  Any ideas?

---

### Post by drs305 on 2008-12-16
Read this, it is the source adult swim mentioned:
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

How to find and delete all the trash on your system.

---

### Post by cdtech on 2008-12-16
For that program just use:
```
trash <file in trash can>
```
To empty all trash just use:
```
empty-trash
```

---

### Post by Arup on 2008-12-16
> **davidself1001 said:**
> I get "Command not found" when I do the sudo empty-trash.  Any ideas?

Did you install trash-cli?

---

