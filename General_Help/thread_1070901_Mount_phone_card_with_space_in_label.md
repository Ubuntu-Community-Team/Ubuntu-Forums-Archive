---
title: "Mount phone card with space in label ?"
date: 2009-02-15
forum: General Help
---

### Post by paulhurleyuk on 2009-02-15
I'm trying to mount my Sony Erricson K800i mobile phone.  This appears as two shares, named 'PHONE' and 'PHONE CARD' in devices recently plugged in (on Kubuntu 8.10 2.6.27-7 generic).

For some reason the UUID AND the device path of these drives chanegs each time they are plugged in, so I'm trying to mount them by the label, the only problem is the space in the PHONE CARD label.  If I give the label with the space, or with single or double quotes then mount reports an error with the fstab file

Under /dev/disk/by-label it is listed as;

```
lrwxrwxrwx 1 root root 10 2009-02-15 20:22 PHONE -> ../../sdc1
lrwxrwxrwx 1 root root 10 2009-02-15 20:22 PHONE\x20CARD -> ../../sdd1
```

If I try PHONE\x20CARD in fstab, then mount reports

```
mount: special device /dev/disk/by-label/PHONE\x5cx20CARD does not exist
```

Is there any way to escape the space ??? (I don't want to re-label the drive, as I it's a new phone I don't want to break !)

Any help gratefully received....

Thanks

Paul.

---

### Post by johnjohn2 on 2009-02-15
Same phone and i don't believe there is

---

### Post by VanillaMozilla on 2009-11-21
Try '\040' (without the quotes) for the space.

---

### Post by VanillaMozilla on 2010-03-12
Much easier is just to use a backslash followed by a space:
"\ " (without the quotation marks).

---

