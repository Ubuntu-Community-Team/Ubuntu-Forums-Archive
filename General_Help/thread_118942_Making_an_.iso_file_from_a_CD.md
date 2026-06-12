---
title: "Making an .iso file from a CD?"
date: 2006-01-18
forum: General Help
---

### Post by PaganHippie on 2006-01-18
Which software would anyone use/recommend?  Burning .iso images *to* CDs is no problem, but I'm having trouble findong an app that goes the other direction....

---

### Post by manicka on 2006-01-18
Right click on the disc on the desktop and choose 'Copy Disc...'.

Write Disc to: File image

---

### Post by PaganHippie on 2006-01-18
That would be too easy.  (Now, why didn't I think of that?)

Thanks!

---

### Post by kaamos on 2006-01-18
Or in terminal:
```
cat /dev/cdrom > image.iso
```

---

### Post by doclivingston on 2006-01-18
[QUOTE=kaamos]Or in terminal:
```
cat /dev/cdrom > image.iso
```[/QUOTE]

You'd probably be better with```
dd if=/dev/cdrom of=image.iso conv=noerror
```

Which will ignore minor disc errors.

---

