---
title: "missing module:: /usr/lib/gnome-vfs-2.0/modules/libcdda.so"
date: 2006-02-24
forum: Desktop Environments
---

### Post by Amleto on 2006-02-24
I frequently get this warning message when using gedit:

```

(gedit:xxxx): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

```

the 'xxxx' is file dependent, and the error occurs when saving a new file.

what is libcdda.so?  What does it do?  How do I get it back?


Thanks

---

### Post by o_fortuna on 2006-02-24
[QUOTE=Amleto]I frequently get this warning message when using gedit:

```

(gedit:xxxx): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

```

the 'xxxx' is file dependent, and the error occurs when saving a new file.

what is libcdda.so?  What does it do?  How do I get it back?


Thanks[/QUOTE]
Try to reinstall libgnomevfs through Synaptic. I don't know if that will fix the problem, but if it's actually preventing you from saving, it's at least worth a try. If it just appears in the terminal, though, and doesn't affect your saving of documents, then I'd ignore it.

---

### Post by Amleto on 2006-02-24
Thanks for the suggestion but I have reinstalled and it hasn't had any affect.   It is just a warning message and doesn't seem to affect the saving of documents.  Sometimes the warning occurs when opening existing files where normal users don't have write permission.

---

### Post by DavidW2 on 2006-02-25
I am getting the error message also and I can't find the module libcdda.so. So I looked for libcdda.so on Gnome's Bugzilla list and found a couple of references to this file.  Bug 315877 mentions this:

Reason: default-modules.conf has "cdda: cdda".
Regardless of whether the cdda module is built, this should not be in
default-modules.conf, because if cdda is built cdda-module.conf will be installed.

So I went to /etc/gnome-vfs-2.0/modules/default-modules.conf and commented out "cdda:cdda".  The warning disappears.  And my cds still play fine.  If anyone finds any detriment to doing this please let us know.

Dave

---

### Post by Amleto on 2006-02-25
Great stuff!  Thanks :)

---

