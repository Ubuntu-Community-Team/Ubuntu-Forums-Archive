---
title: "KDE embedded text editor service?"
date: 2007-10-21
forum: Desktop Environments
---

### Post by Mlehliw on 2007-10-21
Does KDE allow you to embed any text editor you want into certain applications that use kparts?

In System Settings -> Personal -> Default Applications -> Embedded Text Editor it looks like there is such a service but I don't see where you can actually configure the text editor it uses.

I'm using 7.10, ideally I'd like to have vim as my text editor and I'm just trying to see if this is possible.

---

### Post by happysmileman on 2007-10-21
> **Mlehliw said:**
> Does KDE allow you to embed any text editor you want into certain applications that use kparts?

In System Settings -> Personal -> Default Applications -> Embedded Text Editor it looks like there is such a service but I don't see where you can actually configure the text editor it uses.

I'm using 7.10, ideally I'd like to have vim as my text editor and I'm just trying to see if this is possible.

That is only the embedded editor, as in the editor that Konqueror and programs will view text files in, not the default program that opens when you click on a text file, VIM I don't think will work with it as it's not embedded, it's a full program,

To edit the default editor you should probably use the KDE control center (run "kcontrol" in a terminal) and go to "KDE components->File associations", there you can set associations for any file type

---

