---
title: "My trash can has disappeared!"
date: 2006-12-29
forum: Desktop Environments
---

### Post by srgregson on 2006-12-29
I'm using Ubuntu 6.06 Dapper for PPC w/ Gnome.  Today when I was trying to empty the trash  can, I ended up accidentally choosing the "remove from panel" selection and now my trash can icon has vanished.  How do I bring back my trash icon?  Also, I think the trash icon is pretty small and so it is not the easiest to get to, so once I bring it back is there a way for me to make a large trash can shortcut on the desktop?  Any help would be appreciated.

---

### Post by meng on 2006-12-29
Right click on the panel, Add to Panel ...

---

### Post by rajeev1204 on 2006-12-29
hi

If u want a trash icon on desktop  do this


type "sudo gconf-editor"

this opens the configuration editor

go to apps> nautilus >desktop > trashcan icon visible




regards

rajeev

---

### Post by Jensor on 2007-02-23
I tried this:

If u want a trash icon on desktop do this


type "sudo gconf-editor"

this opens the configuration editor

go to apps> nautilus >desktop > trashcan icon visible

then I rebooteed and still no trashcan icon on the desktop.

I can get  a trashcan icon on the Panel at the top of the screen, but so far have not been able to get one on the desktop.

I went to my home folder and made hidden files visible and then created a link to .Trash, then dragged the link to the desktop.  However that is not what I really want.

Does anyone know how to get the icxon there. It would be nice if you could just right click on the desktop and make the appropriate selection.

Jack Ensor

---

### Post by karush on 2007-06-02
Actually i've the same problem.
Removed, not accidentally, the trash from the panel and i've no more icon on the desktop. I tried from gconf-editor but it doesn't work (only for trash,.... it still work for home,volumes,network....). 
I found a way too, making a file  ~/Desktop/Trash.desktop. 

The contents of the file are:

[Desktop Entry]
Comment=Contains removed files
EmptyIcon=trashcan_empty
Encoding=UTF-8
Icon=trashcan_full
Name=Trash
Name[en_US]=Trash
Type=Link
URL=trash:/ 

Anyway i'd like to have the original icon on desktop and not this "workaround".
Any suggestion?

[EDIT] : I solved easily... Just sorted by name Desktop items.... for unknown reason the trash icon was hidden somewhere....

---

