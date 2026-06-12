---
title: "Where are folder properties stored"
date: 2015-07-07
forum: Desktop Environments
---

### Post by chris137 on 2015-07-07
Hi,

I'm using Gnome with nemo on ubuntu 14.04.02.
When doing a right click -> click on the folder-icon I can use a custum one.
My question is: Where is that information stored?

Also, ideally I'd like to make a global config file where I could say "folder /home/chris/folder1 gets icon /home/chris/icons/folder1.ico" something like that.
Is anything like that possible?

Thanks

---

### Post by v3.xx on 2015-07-07
I do not know exactly how to do in ubuntu gnome, but I think you will find the files you are looking for in:
/usr/share/icons 
and 
/usr/share/themes

---

### Post by chris137 on 2015-07-07
Both of these folders are pretty stuffed so I searched the filenames I am currently using for some of my folders.
This information ist not stored there.

---

### Post by v3.xx on 2015-07-07
Also in my system, I have themes in my home folder under ~/.themes

Thats all I got, good luck :)

---

### Post by chris137 on 2015-07-07
No, I don't got that folder at all.
Thanks anyways

---

### Post by mc4man on 2015-07-07
In Ubuntu (using gnome) such info is stored in the  ~/.local/share/gvfs-metadata/home file which is a binary file
(- generally unreadable/not editable
So possibly the same for you, to test either rename that file to a .bak or delete, then log out/in & see..

---

### Post by chris137 on 2015-07-08
At least this file exists :D
It is in fact not readable.
If that's the one would not be of interest in that case. If I can't edit it it has no value to me.
The parts that are readable there might indicate that that info is stored there.

---

### Post by mc4man on 2015-07-09
Seems quite complicated, similar to how gnome moved user setting (gsettings/dconf) to a binary except in that case one can edit/add thru gsettings, dconf, dconf-editor, ect. (and dump the file to text.

Probably not much to be done though you can research...

ex.
```
gvfs-info -w 'metadata::*' .local/share/gvfs-metadata/home
Settable attributes:
Settable attributes:
 standard::symlink-target (bytestring)
 time::access (uint64, Keep with file when moved)
 time::access-usec (uint32, Keep with file when moved)
 time::modified (uint64, Copy with file, Keep with file when moved)
 time::modified-usec (uint32, Copy with file, Keep with file when moved)
 unix::gid (uint32, Keep with file when moved)
 unix::mode (uint32, Copy with file, Keep with file when moved)
 unix::uid (uint32, Keep with file when moved)
Writable attribute namespaces:
 metadata (string, Copy with file, Keep with file when moved)
 xattr (string, Copy with file, Keep with file when moved)
 xattr-sys (string, Keep with file when moved)
```

---

### Post by vasa1 on 2015-07-09
> **chris137 said:**
> Hi,

I'm using Gnome with nemo on ubuntu 14.04.02.
When doing a right click -> click on the folder-icon I can use a custum one.
My question is: Where is that information stored?

...
[http://www.webupd8.org/2015/03/nautilus-nemo-and-caja-extension-folder.html](http://www.webupd8.org/2015/03/nautilus-nemo-and-caja-extension-folder.html) may offer some pointers.

---

### Post by chris137 on 2015-07-09
Well that's a step in the right direction at least.
I think it might be possible to use custom icons there (not a feature of this per se!) but I guess I'd still have to apply it to every folder by right click -> use icon.

---

