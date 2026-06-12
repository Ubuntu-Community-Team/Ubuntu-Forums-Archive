---
title: "Wrong default application : very annoying"
date: 2009-10-05
forum: Desktop Environments
---

### Post by roy.nico on 2009-10-05
Hej everybody.

I updated recently from 8.04 to 9.04 byformatting the / partition, installing the new ubuntu, but keeping the old /home partition. 
When i clic on the gnome menu "Shortcuts/home folder", it starts Baobab (Disk Usage Analyzer) instead of Nautilus as expected. The same for all shortcuts Video, Music, and so on... very annoying. To see my home folder, i need to open a terminal and start nautilus manually.

Any idea to fix this will be (very) welcome :)
Thanks in advance, 

nicolas

---

### Post by SlugSlug on 2009-10-05
goto places > computer in left panel click home in right panel right click Desktop > open with > file browser

that should fix it...

---

### Post by roy.nico on 2009-10-06
Thanks for the answer. 

But it doesn't work.

* Places/Computer opens indeed Nautilus, then everything works normally, double clic on a folder will open the folder.
* But Places/home opens baobab.
* The same for Places/bookmarks/Video (or Music, ...)

nicolas

---

### Post by SlugSlug on 2009-10-06
> **roy.nico said:**
> Thanks for the answer. 

But it doesn't work.

* Places/Computer opens indeed Nautilus, then everything works normally, double clic on a folder will open the folder.
* But Places/home opens baobab.
* The same for Places/bookmarks/Video (or Music, ...)

nicolas


what if you right click it open with then always use this application and select the file browser 

am not on my pc at the mo so cnt find correct way, but it will work as I did it recently to my dads..

---

### Post by roy.nico on 2009-10-07
Hej !

> **SlugSlug said:**
> what if you right click it open with then always use this application and select the file browser 

If i right clic on Places/computer, there is no menu, it open Nautilus on "computer:///", as i said before.
If i open Nautilus (with command line), on the left panel clic on home/my_name, and on the right panel clic on "open with", i have a list of applications that i can choose, but no such option like "always use this application"...


nico

---

### Post by roy.nico on 2009-10-07
This was actually a bug, which appear when one has several possible applications associated to folders, under  Hardy, and one updates to Jaunty for exemple. See [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/366963](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/366963)
* Unfortunately, it is not possible to fix this thru le menus, because in Jaunty, the tab "open with", in the "properties" window of folders is no longer available. 
* To fix it, modify per hand the file .local/share/applications/mimeapps.list . On the line starting with "inode/directory", make the option "nautilus-folder-handler.desktop;" as the first one.

Hope this will help others.

Nico

---

