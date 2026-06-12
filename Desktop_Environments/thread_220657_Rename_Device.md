---
title: "Rename Device"
date: 2006-07-21
forum: Desktop Environments
---

### Post by moore.bryan on 2006-07-21
many have posted, almost none have answered... how can one rename a device?  for example, ubuntu thinks my external usb hard drive is named "USB HD."  because of the space in between the "B" and "H," i can't access it through terminal.  any ideas?

---

### Post by scxtt on 2006-07-21
how are you trying to do it?

try typing:

cd /path_to_device_mount/USB\ HD --> cd /media/USB\ HD
- or -
cd /path_to_device_mount/"USB HD" --> cd /media/"USB HD"

---

### Post by moore.bryan on 2006-07-22
will quoting the term in terminal (i.e. "USB HD") allow me to access it or will using the backslash act as a space?

---

### Post by Janux on 2006-07-22
You need to type between quotes the full path
```
cd '/media/USB HD'
```

You can also use the tab button when you are writing a path on the terminal.
Let's say:
```
cd /media/USB<tab>
```
and the full path will be autocompleted

---

### Post by bukwirm on 2006-07-22
> **moore.bryan said:**
> will quoting the term in terminal (i.e. "USB HD") allow me to access it or will using the backslash act as a space?

Either should work.

You could also make symbolic link, i.e. ln --symbolic "USB HD" usbhd
Then you can just use usbhd.

---

### Post by moore.bryan on 2006-07-22
> **bukwirm said:**
> Either should work.

You could also make symbolic link, i.e. ln --symbolic "USB HD" usbhd
Then you can just use usbhd.

thanks bukwirm... seems like this is the simplest/easiest way.  i'll try this out.

EDIT

worked like a charm... thanks!

---

