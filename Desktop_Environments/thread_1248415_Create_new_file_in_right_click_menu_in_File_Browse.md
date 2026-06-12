---
title: "Create new file in right click menu in File Browser"
date: 2009-08-24
forum: Desktop Environments
---

### Post by Zeemvel on 2009-08-24
Hi,

When a folder doesn't have a lot of files in it, there's a white zone in the File Browser. If I right click in that white zone, I get a right-click menu that allows me to create new folder, create new file, ...

If however the folder has so much files that a scrollbar is needed, then the whole window is taken up by files, there's no white zone. Right clicking shows options for the file your mouse was hovering over. Is there any way at all to get the other right click menu?

---

### Post by ajgreeny on 2009-08-24
You will have to do it in the **File >Create Document>Empty file** having navigated to the folder you want to put the empty file in.  I don't think you can do it with a context menu, I'm afraid.

---

### Post by mcduck on 2009-08-24
> **Zeemvel said:**
> Hi,

When a folder doesn't have a lot of files in it, there's a white zone in the File Browser. If I right click in that white zone, I get a right-click menu that allows me to create new folder, create new file, ...

If however the folder has so much files that a scrollbar is needed, then the whole window is taken up by files, there's no white zone. Right clicking shows options for the file your mouse was hovering over. Is there any way at all to get the other right click menu?

Try using the icon (or small icons) view. There's always enough space to open the right-click menu.

---

### Post by ajgreeny on 2009-08-24
Not always!  I have a few folders with huge numbers of files (photos, generally) that still fill the whole screen even when using the smallest icons in compact view.

---

### Post by Seankn on 2009-08-24
It works...

---

### Post by mcduck on 2009-08-25
> **ajgreeny said:**
> Not always!  I have a few folders with huge numbers of files (photos, generally) that still fill the whole screen even when using the smallest icons in compact view.

There's always space *between* the icons. Both Icons- and Compact-modes have some amount of padding around the icons regardless of the icon size you use. Even if you set Nautilus to use compact layout.

The only setup where you might not have space is a directory that contains large number of files, viewed in the List-mode.

---

### Post by Wardje on 2009-08-25
Speaking of which, is there a way to get around this if you -are- in list view?

---

### Post by mcduck on 2009-08-25
> **Wardje said:**
> Speaking of which, is there a way to get around this if you -are- in list view?

Use the File->Create Document from the menu.

---

### Post by ajgreeny on 2009-08-25
> **mcduck said:**
> There's always space *between* the icons. Both Icons- and Compact-modes have some amount of padding around the icons regardless of the icon size you use. Even if you set Nautilus to use compact layout.

The only setup where you might not have space is a directory that contains large number of files, viewed in the List-mode.
Yes, you are correct!  Not something I knew, or so far have needed to know, but all knowledge is useful, so thanks for that little gem.

---

### Post by Naater on 2009-08-25
this is what I would do to create files if there isn't room:

-I would create the file in under desktop
-then go to file browser
-right click new file
-click "cut"
-then 'paste" where-ever


That or make the window bigger.

---

### Post by Wardje on 2009-08-26
> **mcduck said:**
> Use the File->Create Document from the menu.

Well obviously you can do that, I'm talking about a way to be able to get the folder context menu by right clicking somewhere in the folder.

---

### Post by Naater on 2009-08-26
That's what I suggested. Make it somewhere where there is "space" and then cut and paste it.

---

### Post by Naater on 2009-08-26
> **Wardje said:**
> Well obviously you can do that, I'm talking about a way to be able to get the folder context menu by right clicking somewhere in the folder.
My anwser is the same. Make a folder somewhere else where there is "space" and then cut and paste it.

---

### Post by Naater on 2009-08-26
Gosh! sorry for triple posting and ruining everything! I ment to edit it and instead I made a new one somehow.

---

### Post by Wardje on 2009-08-27
That pretty much defeats the whole point of making it easier to access, Naater.

Similar problem with dragging a folder/file into a folder that only has folders (and has enough of them to have no whitespace left), you can't deposit it anywhere since that will paste it in one of the subfolders. (You can drop it in the current folder's icon in the location bar, but that fails when you have the location bar set to show the actual path)

---

### Post by mcduck on 2009-08-27
> **Wardje said:**
> That pretty much defeats the whole point of making it easier to access, Naater.

Similar problem with dragging a folder/file into a folder that only has folders (and has enough of them to have no whitespace left), you can't deposit it anywhere since that will paste it in one of the subfolders. (You can drop it in the current folder's icon in the location bar, but that fails when you have the location bar set to show the actual path)

In that case the solution is simply to move one step up in the directory hierarchy (instead of having the directory where you want to drop the file open you'd have open the directory in which the target directory is). Now you can drop the file into that directory's icon.

Anyway, I rarely use the list view because it doesn't really work well in this kind of situations. Instead I use the icon view, and configure it to show the info I want under the icons. (file/directory sizes at 100% zoom level, and permissions at 150%).

(Besides, I prefer using Nautilus in spatial mode and list view doesn't really fit into that anyway.)

---

