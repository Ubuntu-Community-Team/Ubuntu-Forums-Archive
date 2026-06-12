---
title: "Nautilus desktop icons"
date: 2010-01-08
forum: Desktop Environments
---

### Post by Stuart P. Bentley on 2010-01-08
Where does Nautilus store desktop icon positions in Karmic? Most sites listed it as being in ~/.nautilus/metafiles/Desktop.xml, but ~/.nautilus is empty in Karmic.

---

### Post by Stuart P. Bentley on 2010-01-15
Anyone?

---

### Post by nunovi on 2010-01-27
Just bumping this as I have the same problem. Anyone? Please?

---

### Post by jaesjg on 2010-01-27
Don't know if this is what you want

/usr/share/icons

---

### Post by t.rei on 2010-01-27
Im not quite shure but probably somewhere in gconf? 

Try looking around in gconf-editor 

For me it stores the icon positions to whereever I put them. Never wondered really on how to change those on config level.

---

### Post by tumipetteri on 2010-01-28
Looks like at least all my desktop filenames are found in binary file ~/.local/share/gvfs-metadata/home . Not sure how to edit though. My problem is not being able to move my desktop icons to another screen :/

---

### Post by produnis on 2010-04-30
I have a similar problem with an empty .nautilus/metafile

I need to backup all emblems I attached to files..
Well, not the icons themselves, but the information WHICH emblem was attached to WHICH file...
[http://ubuntuforums.org/showthread.php?t=1466565](http://ubuntuforums.org/showthread.php?t=1466565)

---

### Post by gachen on 2010-05-03
I have the same question..
I read the source code, but still confused..

In fm-icon-view.c ,there is a comments like this:
/* If it is the desktop directory, maybe the gnome-libs metadata has information about it */

but this doesn't help, what is gnome-libs? too old ?

---

### Post by gachen on 2010-05-03
I debug quite some time , and found that nautilus use g_file_set_attributes_async() to store position info of icons. (at least for desktop)

key = "metadata:nautilus-icon-position"
value is the x,y of the icon.

so , I need some more time to figure out how the info is stored. Or somebody else can help?

---

