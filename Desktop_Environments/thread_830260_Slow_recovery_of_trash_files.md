---
title: "Slow recovery of trash files"
date: 2008-06-15
forum: Desktop Environments
---

### Post by Habbit on 2008-06-15
I'm having an annoying problem with the "trash" feature of GNOME in Hardy: recovering files from the Trash (meaning cut/copy a file from the Trash and paste it elsewhere) takes just as a normal file copy, which is absurd taking into account that moving files _to_ the Trash does not.

At fist I considered the possibility that my Trash folder were in a different partition as my destination directory, but I found that both are in my /home partition. However, I think that either Nautilus or gvfs are failing to notice such eventuality when I request the operation, and thus a copy between the "gvfsd-trash" server and whichever one handles local-filesystem operations is being performed. I fail to guess why this does not happen when I send files _to_ the Trash too.

I would like to know whether there's any workaround (apart from opening the "true" Trash folder at ~/.local/share/trash and working with it) and if I should file a bug on this. I usually work with multi-gigabyte files, and waiting five minutes for an unnecessary copy to be performed is just a no-go. I praise gvfs and its modularity, but this is a regression on past behavior, and a serious one.

---

### Post by Habbit on 2008-06-15
Er... bump?

---

### Post by Bubba64 on 2008-06-15
I think what you may be missing is that if something is in the trash the file exists somewhere else is just the header in the trash, that is my theory anyway.

---

### Post by Habbit on 2008-06-16
> **Bubba64 said:**
> if something is in the trash the file exists somewhere else is just the header in the trash.
Nope, the whole file gets moved to a Trash folder, in my case ~/.local/share/Trash, with the file going in the "files" folder and a metadata file containing the original path and the deletion date in the "info" folder. Which is even more irritating, since Nautilus has no "obvious" way to restore a file to its original path with one or two clicks like windoze has.

---

### Post by rfugger on 2008-07-13
I'm having the same problem.  I say open a bug.

---

### Post by Mihai Chezan on 2008-09-20
I have the same problem: when I try to "cut" a file from "Trash" and then "paste" to another folder Nautilus starts to "copy" the file instead of "move" it (the source and destinations are on the same partition; if I do the same operation from GNU Midnight Commander is works as it should be, a "move" operation is used instead of "copy").

Was a bug open?

---

