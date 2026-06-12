---
title: "Which permission to make a directory tree undeletable for me?? (Arrg! Lost data!)"
date: 2007-09-03
forum: Desktop Environments
---

### Post by isync on 2007-09-03
Ext3 has great features, and being not able to undelete things is one of them - I think.

But the nautilus file explorer window is a pain for someone coming from windows. When you select a file by single click - you start it. When you select with CTRL+<you name it> I tend to add the selection to previously used directories and when I delete them I delete the previously selected directory with them!

OK. I learned my lesson. After I lost a *huge* directory tree due to this behaviour I would like to make important directories writable for my user, but not deletable - is that possible?

---

### Post by EvergreyNY on 2007-09-04
Right click on the main directory and under Permissions, change folder access permission to Access files. That folder itself will not be able to be deleted, but subfolders will be (unless you apply permissions to all subfolders). You will still have full read/write permission for files contained. 

In youf file manager, head up to the Edit menu and select Preferences. Under the Behavior tab, you should be able to choose between single click or double click to open files and folders.

---

### Post by isync on 2007-09-04
Thanks for the reply and steps!

(BTW: I knew it would be possible to customize nautilus... Argh! [Should have known earlier...] )

---

### Post by isync on 2007-09-04
> **EvergreyNY said:**
> Right click on the main directory and under Permissions, change folder access permission to Access files. That folder itself will not be able to be deleted, but subfolders will be (unless you apply permissions to all subfolders). You will still have full read/write permission for files contained. 

Setting to "access files" is not quite clear for me... I set permission for a folder from octal 0755 to 0444 which locked the folder, more like it freezed it. I could open files, but I could not change files contained in it. So perm seems to be recoursive - at least on first level: I did not check if files in a subfolder of the changed folder inherited the 0444...

So is it possible to just remove the "delete" rights but allow creation, read and modification?

---

### Post by ayoli on 2007-09-04
access files means only readeable, opposite ist create and delete files, but I m affraid that you can separate create and delete rights.

---

### Post by astralsin on 2007-09-04
ReiserFS has some really nice undelete/data recovery features.  You can do it in Ext3 somehow but its fairly complicated.  I suggest switching over to Reiser if data loss is a concern

---

### Post by daengbo on 2007-12-27
I'm a little confused. The default settings for Nautilus in Ubuntu are for single-click to select and double-click to open. Have you changed that somewhere?

---

