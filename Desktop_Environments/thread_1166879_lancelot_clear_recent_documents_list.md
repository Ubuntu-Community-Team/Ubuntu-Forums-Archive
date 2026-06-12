---
title: "lancelot clear recent documents list"
date: 2009-05-22
forum: Desktop Environments
---

### Post by allaf on 2009-05-22
Hi,

Looks like there's a very annoying missing feature in lancelot, there is no way to clear the recent documents list.
I tried manually removing files from /.kde/share/apps/RecentDocuments/ but it doesn't work.


KDE: 4.2.2 (KDE 4.2.2)
Lancelot: 1.5

---

### Post by viking_maniac on 2009-10-31
I know that this thread is a bit old, but I just discovered the same thing in Kubuntu Karmic. I really miss the "clear all history" feature that you have in Gnome, that clears all history on your computer including all apps installed.

I tried Sweeper for KDE, but just as in Gnome, it only does the job halfway, and that's not good enough. I think Sweeper should be removed from the repositories. It just doesn't work.

If anyone know about any other programs that fixes this privacy issue in KDE, I'd be very happy!

---

### Post by Zorael on 2009-10-31
I'm not sure if it works in Lancelot, but in the normal menu you can just right-click anywhere in the Recently Used view and pick Clear Recent Applications/Documents.

edit: from [http://forum.kde.org/viewtopic.php?f=67&t=62112#p81616](http://forum.kde.org/viewtopic.php?f=67&t=62112#p81616)
> option to clean also available in Lancelot
Also in the same thread;
> solution: type in terminal
rm ~/.kde/share/apps/RecentDocuments/*&&chmod 000 ~/.kde/share/apps/RecentDocuments
That command would clear Recent Documents and write-protect the directory, disabling it from getting new entries. If you just want to clear it, perform only the first half.
```
$ rm ~/.kde/share/apps/RecentDocuments/*
```

---

