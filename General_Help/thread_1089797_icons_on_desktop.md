---
title: "icons on desktop ?"
date: 2009-03-07
forum: General Help
---

### Post by fa355115 on 2009-03-07
Hi there !

I'm coming from vista where it is possible to put icons (for drives for example) on the desktop.
On ubuntu, each time I get a location from "places", it is put on the desktop, but then removed when I shutdown and switch my PC back on ...

I am missing something here ?

Thank you !

---

### Post by UbuntuNerd on 2009-03-07
Im not sure about the drives but you can add trash icon, network icon, home icon and computer icon by typing this in a terminal:
```
gconf-editor
```
Now browse down to this key: apps \ nautilus \ desktop
On the right side look for the entries you want visible and check the box beside of it.

---

### Post by fa355115 on 2009-03-08
> **UbuntuNerd said:**
> Im not sure about the drives but you can add trash icon, network icon, home icon and computer icon by typing this in a terminal:
```
gconf-editor
```
Now browse down to this key: apps \ nautilus \ desktop
On the right side look for the entries you want visible and check the box beside of it.

"Command not found" ?!?

---

### Post by hyperdude111 on 2009-03-08
The icons on your desktop are the MOUNTED removable drives they only show up if you have already used the drive.

If you want to add icons for "Computer, Home and trash etc. Download Ubuntu tweak it will lt you change those settings without the complicated gconf -editor

Link for ubuntutweak - [http://www.getdeb.net/app/Ubuntu+Tweak](http://www.getdeb.net/app/Ubuntu+Tweak)

---

