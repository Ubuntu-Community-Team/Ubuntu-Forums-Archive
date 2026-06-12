---
title: "nautilus-gksu &quot;Open as administrator&quot; doesn't work on drives"
date: 2009-09-10
forum: Desktop Environments
---

### Post by osx on 2009-09-10
I like using the nautilus-gksu package to be able to right-click on a folder/file and select "Open as administrator" to browse/view files and folders as root. A lot more convenient than having to drop to terminal.

However, when I tried to do this on a mounted thumbdrive by right-clicking on the drive's icon on the desktop, I do not get the "Open as administrator" option. If I first browse the drive, I can right-click a folder, but I want to be able to browse anywhere on the drive by applying the option once to it and not having to do it for every folder.

Is this by design or a bug?

Thanks.

---

### Post by ajgreeny on 2009-09-10
You should be able to do it by browsing to /media, where the drive is mounted, in the left hand pane of nautilus and then right clicking on the mount folder for the drive in the right hand panel of nautilus as normal.  I'm certainly not aware of any reason why this will not work in the same way as it does for other drives accessed in this way.

---

### Post by osx on 2009-09-10
> **ajgreeny said:**
> You should be able to do it by browsing to /media, where the drive is mounted, in the left hand pane of nautilus and then right clicking on the mount folder for the drive in the right hand panel of nautilus as normal.  I'm certainly not aware of any reason why this will not work in the same way as it does for other drives accessed in this way.

That does work (thanks, I hadn't even thought of that), but I was hoping for the quicker method of using the desktop icon. Guess it will have to do for now.

---

### Post by ajgreeny on 2009-09-10
Just to try it out, I just tried making a desktop link to the /media/WindowsXP folder on my machine.  No problem with that, nor with the *Open as administrator* being present in the context menu, but unfortunately it did not work, saying it was not possible to work out which application to use to do it.  If you can search on how to do that, you may just be able to get the thing to work as you want.

Over to you!

---

