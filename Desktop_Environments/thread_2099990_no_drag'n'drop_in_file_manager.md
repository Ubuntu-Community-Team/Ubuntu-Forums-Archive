---
title: "no drag'n'drop in file manager"
date: 2012-12-31
forum: Desktop Environments
---

### Post by engine on 2012-12-31
The title says it all &#8210; I can't simply drag'n'drop to move files between directories in the file manager. (come to that, I can't even use a right-click to copy: have to go up to the menu bar) Are these lubuntu features, or is there something a bit wrong with my installation?

---

### Post by vasa1 on 2012-12-31
Well, you could mention the version of Lubuntu you are using.

---

### Post by vasa1 on 2012-12-31
One thing is that you need to left click on the area under the "Name" column to drag-n-drop. Clicking anywhere else won't do anything.

Right-clicking to open a context menu (which includes copy) works anywhere in the row.

---

### Post by engine on 2012-12-31
Right-click in the Name/Description pane gives me a context menu where I can copy the selected file, but right-click on the destination folder in the directory tree doesn't give any context menu. Right-click in the Places list (which would be about as useless as the Mac finder, because it doesn't allow navigation to a folder) does not give the corresponding paste option.

I'll be delighted to say what version of Lubuntu I'm running, if someone can tell me how to find out!

---

### Post by vasa1 on 2012-12-31
This at least should give some clue:
```
lsb_release -a
```

---

### Post by Rex Bouwense on 2012-12-31
To find out which version that you are using, open a terminal and type:
```
lsb_release -a
```
and then enter.  Your version will be on the line that says Description.

---

### Post by vasa1 on 2012-12-31
> **engine said:**
> Right-click in the Name/Description pane gives me a context menu where I can copy the selected file, ...
So you **can** copy with a right-click. That isn't what you wrote in the first post.

---

### Post by vasa1 on 2012-12-31
And once you click on a folder in the places column, move back to the space on the right and right-click to paste.

---

### Post by Dennis N on 2012-12-31
> **engine said:**
> Right-click in the Name/Description pane gives me a context menu where I can copy the selected file, but right-click on the destination folder in the directory tree doesn't give any context menu. Right-click in the Places list (which would be about as useless as the Mac finder, because it doesn't allow navigation to a folder) does not give the corresponding paste option.



You cannot drag and drop to the side pane or do your paste command there - only into the main window. My suggestion for move/copy file (or directory) is to open the destination folder in a **new tab** if it is not also in the same main window, then **drag** the file/directory up to new tab, which will then be switched to if you pause a moment, then down to the main window to drop in any folder there. 

Yes, there is no copy button on the tool bar of pcmanfm. Either rely on the right-click menu, or use the main Edit menu.

The PCmanfm in Lubuntu 12.10 has big improvements over the older version. The developer is doing an excellent job. Very solid in my opinion.

---

### Post by TenPlus1 on 2012-12-31
Using Lubnutu and the file manager PcManFm dragging and dropping is a little different, you select using the mouse first then let go of the left button and click again to DRAG and move the selected files...  The newer Lubuntu 12.10 will let you drag n drop a lot easier though...

---

