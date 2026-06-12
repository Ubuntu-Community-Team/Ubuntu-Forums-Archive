---
title: "Lockup when emptying trash"
date: 2009-06-24
forum: General Help
---

### Post by jdeppel on 2009-06-24
Hey all...I tried searching for this...but did not find anything of use...at least not with the search terms I used...

Anyways, I'm using Jaunty 9.04, and every time I empty the Trash can, my system locks up, forcing me to hard reboot. If I permanently delete files, rather than moving them to trash (SHIFT+DEL), that works. But any time I have files in the trashcan, I click "Empty Trash" and about 5 seconds later, I lockup.

I even tried a reinstall and that didn't seem to change anything. 

Any ideas?
:confused:

---

### Post by blueridgedog on 2009-06-24
Do you get the same effect if you delete the trash files by hand?

```
rm ~/.local/share/Trash/* -rf
```

---

### Post by geirha on 2009-06-24
Are you using ext4? If so, see [Lock-ups when deleting files from ext4 filesystems]("http://www.ubuntu.com/getubuntu/releasenotes/904#Lock-ups when deleting files from ext4 filesystems")

---

### Post by jdeppel on 2009-06-24
Okay. Emptied the trash from the terminal, and we still locked up. 

I was unaware there was a bug reported for this, thanks for the link.

However, I can delete files (either using SHIFT+DEL from the GUI, or rm command in terminal) and no lockup occurs. Just if I send a file to the trash and empty it, I'm hosed.

I guess I can just restore files from the trash for now until a bug fix is released.

---

### Post by wpshooter on 2009-06-24
> **geirha said:**
> Are you using ext4? If so, see [Lock-ups when deleting files from ext4 filesystems]("http://www.ubuntu.com/getubuntu/releasenotes/904#Lock-ups when deleting files from ext4 filesystems")

Must be only in certain circumstances.

I am using Ext4 on Jaunty and I just deleted some files and then emptied the trash bin and well I am still able to make this post !!!

---

### Post by jdeppel on 2009-06-24
Not me. I even just created one "dummy" text file w/o any text it in...and that managed to lockup the system when I attempted to empty it from the trash.

Restored it, and did a SHIFT+DEL on it...and *poof* it's gone, no problem.

---

### Post by blueridgedog on 2009-06-24
Well, if you have the disk space and can create an ext3 partition, you could prove the 3 vs 4 issue easily.

---

### Post by philcamlin on 2009-06-24
odd that mine works nice

---

### Post by jdeppel on 2009-06-24
Actually, I may have found the problem.

In ~/.local/share/Trash/expunged I found a folder (1663581034 it was named) that is holding EVERY file I've ever deleted since this "bug" appeared for me it seems. The folder is 9.6GB in size. Currently, I'm deleting each and every file individually (i tired to rm -Rf * which caused a lockup) and will report back.

---

### Post by jdeppel on 2009-06-25
Viola! That was it...deleted all those files...and now I can empty trash without issue.

As I've never had to delve that far into the "trash directory," how/why did those files end up in that "expunged" directory?

---

### Post by blueridgedog on 2009-06-25
Do a search on launchpad.  I did and I found this pretty quick by Andrew Ziem "files can be stuck in here if Nautilus deletes a folder that belongs to you but contains files that don't, and it is tricky for Nautilus to handle this situation correctly."

There may be more information, but at least you found the cause and know how to deal with it.

---

