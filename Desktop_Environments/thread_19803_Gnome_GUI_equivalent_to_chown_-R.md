---
title: "Gnome GUI equivalent to chown -R"
date: 2005-03-13
forum: Desktop Environments
---

### Post by steffen on 2005-03-13
I've been looking around for a Gnome GUI point-and-click equivalent of chown -R

The reason why this is important, is that when files are copied from a CD, the permissions are inherited, so all of them are write protected. To go through every file and right click and find the permissions tab in properties and clicking on write access for the owner, is tedious. Therefore one has to use console. To newbies this seems awkward, and therefore there should be a Gnome command for this.

1) Does anyone know where in Gnome this can be found?

2) Does anyone know how to make files copIed from a CD to automatically be writable by the owner?

---

### Post by bored2k on 2005-03-13
[QUOTE=steffen]I've been looking around for a Gnome GUI point-and-click equivalent of chown -R

The reason why this is important, is that when files are copied from a CD, the permissions are inherited, so all of them are write protected. To go through every file and right click and find the permissions tab in properties and clicking on write access for the owner, is tedious. Therefore one has to use console. To newbies this seems awkward, and therefore there should be a Gnome command for this.

1) Does anyone know where in Gnome this can be found?

2) Does anyone know how to make files copIed from a CD to automatically be writable by the owner?[/QUOTE]
 1.Right clic > properties on a file > permissions > owner tab

2. Not sure, you can always chmod a+x the files or do it in GUi.

---

### Post by rosslaird on 2005-03-13
KDE used to have a recursive option for file permissions, but I'm not sure if the most recent version still has it. Gnome has no such feature (AFAIK). In Gnome, you're stuck with one directory/file at a time. Someone please correct me if I'm mistaken.

---

### Post by steffen on 2005-03-14
Sorry guys - I actually meant chmod -R 755 owner

Anyone know how to automatically set files copied from a digicam or CD to 755?

---

