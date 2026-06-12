---
title: "New mini 9/Ubuntu owner"
date: 2009-04-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by marmaduke01 on 2009-04-09
Hi all. I've had my min 9 for 5 days now and am loving it.
Couple of questions please. Running the 8.04 remix version. Have switched to classic mode. 

How do I delete several items in the trash. I haven't found a "delete all" button, so I end up hi-lighting each file then deleting each file. 

In Windows XP if you right click on the Start button, then left click on Explore, you end up in the file manager/explorer window for all the files/directories on the hard drive.  Is there an easy way to do the same thing in Ubuntu?  

Does Ubuntu show the SSD as a "C" drive?  I plan on plugging in a SDHC card and want to start directing downloads to it. Just want to know what to look for when its plugged in.  "D" ???

Any way to find total size of SSD and space used or free?  I'm looking at something but the numbers don't add up.  Supposed to be a 8 Gig SSD. 

Thanks for any help.

---

### Post by shof2k on 2009-04-09
> How do I delete several items in the trash
If you can see the trash icon, right click and select empty

> Does Ubuntu show the SSD as a "C" drive?  I plan on plugging in a SDHC card and want to start directing downloads to it. Just want to know what to look for when its plugged in.  "D" ???
If you plug in an SDHC card, you'll see another icon called something like '8 GB disk'

> 
Any way to find total size of SSD and space used or free?  I'm looking at something but the numbers don't add up.  Supposed to be a 8 Gig SSD. 


Two ways to do this I can think of.  First use the disk usage analyser.  Second, open a terminal and type
```

df -H
```

hope that helps

---

### Post by Ryback on 2009-04-09
> **marmaduke01 said:**
> How do I delete several items in the trash. I haven't found a "delete all" button, so I end up hi-lighting each file then deleting each file.

Hey, welcome.  I'm using the dell supplied OS too.  When in Nautilus (the file browser) and viewing the wastebasket/deleted items folder, there should be an option that says "Empty Deleted Items" at the top of the file list.

Also, if you don't have a wastebasket icon on your desktop, you can add one by opening a terminal and running 
```
gconf-editor
```

Then going to apps -> nautilus -> desktop and check the trash_icon_visible box.

---

### Post by marmaduke01 on 2009-04-09
Thanks for the help. Only thing I have showing on my desktop right now is a Dell folder with a lot of paperwork regarding my purchase.  Warranties, repairs, stuff like that. Have to add Trash then.

---

### Post by ugm6hr on 2009-04-09
If using Classic Mode:

1. Empty Trash:
Places -> Home Folder
This opens File browser aka "nautilus"
In the left hand panel (Press Fn+L if you don't have one), ensure the drop-down says "Places" and look for "Deleted Items" in the list
Right-click "Deleted Items" -> Empty Deleted Items OR
Left-click "Deleted Items" and use the Empty Deleted Items button at the top

2 To delete multiple files:
Open the relevant folder in nautilus
Drag-select or use Shift / Ctrl-click to select multiple files.
Press Delete key, or right-click on one selected file -> Move to the Deleted Items Folder

3. SDHC cards are given the location /media/disk, but appear in nautilus as 8GB disk in "Places"
You can change that by renaming the SD card. e.g. if the card is named "sdhome" - it will have the location /media/sdhome (as mine does), and appear in nautilus as "sdhome".
If you plan to use the SDHC as a regular location for downloads with Ubuntu, consider formatting it with Ubuntu as ext2 (as I have).
In any case, you can create a "symlink" from your "Home Folder" to the SDHC, making it easier to find.

4. shof2k has covered this fully

---

