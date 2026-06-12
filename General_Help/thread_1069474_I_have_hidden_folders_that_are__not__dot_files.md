---
title: "I have hidden folders that are _not_ dot files ???"
date: 2009-02-14
forum: General Help
---

### Post by jyaan on 2009-02-14
I have a couple folders on my hard disk that do not show up unless I enable the display of hidden files/folders. However, their filenames do *not* begin with a period! I have been wondering *how this happened, and how it is even possible!!*.

The folders have the *exact* same permissions as the others that are visible (**drwxr-xr-x**; parents are the same as well).

Does anyone know what is going on here?? The filesystem is Ext3.

Edit: I found that it is not hidden when I use ls. It is still hidden in Nautilus, though...

---

### Post by sujoy on 2009-02-14
do the filenames end in "~" ? these files are hidden in nautilus somehow
edit: file ending in ~ are hidden in thunar too

---

### Post by jyaan on 2009-02-14
Ah, that's what it was. Yep, the filenames ended it ~

Thanks.

---

### Post by sdennie on 2009-02-14
You can also make files hidden in Nautilus by putting a file/directory name one per line in a file called .hidden.  This is useful if you know you are only going to use nautilus to manipulate a few directories and want to remove the clutter to only see those directories.

---

