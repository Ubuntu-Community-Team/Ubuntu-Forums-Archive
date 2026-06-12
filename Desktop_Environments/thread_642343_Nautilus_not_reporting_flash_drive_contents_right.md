---
title: "Nautilus not reporting flash drive contents right?"
date: 2007-12-16
forum: Desktop Environments
---

### Post by jorwex on 2007-12-16
Hey all,

for the first time since switching from xp, I was trying to put some files on my flash drive so I could use them on my xbox with XBMC. I popped in my flash drive, and there was not enough space for my files, so I went to delete some big files. after making space, I went to the .Trash-jorwex folder, or whatever it's called, and permanently got rid of them. 

STILL tho, I didn't have enough space, even tho when I looked at the remaining few files, folders and highlighted them all (even with 'show hidden files' checked), only amounted to a few kb or mb. anyway, here's the proof:

Note: the files I wanted to copy totalled about 850 megs--usually about 915 or so is the max for that flash drive.
[IMG]http://www.wam.umd.edu/~jwexler/blah.jpg[/IMG]

Weird eh? I checked FIVE times to make sure that the .Trash folder was empty.

I ended up just reformatting the drive after copying what I needed to a safe place. I used gparted and did fat32 like before (tho i couldnt figure out how to enable vfat). it recognized in XBMC but it didnt show the files I copied before (which woulda been the only contents by then). i went back to my pc and the files were indeed on the drive. 

I'm lost

---

### Post by cammin on 2007-12-17
Unmount the drive then re-mount it.

If that works, there should be an option to disable write caching for removable drives.

---

### Post by jorwex on 2007-12-17
wheres that option? 
does the fact that i unmounted and then remounted have any bearing on that setting becoming visible?

---

### Post by chronic on 2007-12-18
as far as i know it doesnt actually write the data to the flash drive when you copy files to it it does that when you click unmount

:lolflag:

---

