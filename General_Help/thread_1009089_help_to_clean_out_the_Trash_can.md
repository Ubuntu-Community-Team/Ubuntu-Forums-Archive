---
title: "help to clean out the Trash can"
date: 2008-12-12
forum: General Help
---

### Post by Cahan on 2008-12-12
Howdy and a week ago I pulled a data file off of a CD that I had (old back up) but it was done with a old linux install after I got the data I needed I drop it in to the trash and at the end I went to emepy the trash but I was told I can not do it. so how do I use sudo to do it and delete it out of the trash can

Thank you for you time on this

---

### Post by Poyntz on 2008-12-12
1. Drop the files in trash onto your desktop
 2. Open a terminal
3. Type: ```
cd ~/Desktop
``` - changes to the Desktop directory
4. Type: ```
rm <filename> <filename>
```
or if all files have the same extension
5. Type: ```
rm *.<extension>
``` - removes all files with that extension
eg, rm *.jpg will remove all the .jpg files
6. If it says you need admin privs type: ```
sudo !!
``` then enter in your password

---

### Post by Cahan on 2008-12-15
Howdy and I can copy it out but it will not let me move it out after copy I did what you said to and the copy was delete ok but the one that was still in there is still given me a Permission denied to do any thing to it

PS it is a Folder with 6 sub-Folders in it (close to 160MB of Doc files)

---

### Post by Cahan on 2009-01-17
[SOLVED] thanks

---

