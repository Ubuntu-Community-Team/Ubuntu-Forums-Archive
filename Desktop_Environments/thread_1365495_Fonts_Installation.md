---
title: "Fonts Installation"
date: 2009-12-27
forum: Desktop Environments
---

### Post by trintin7 on 2009-12-27
I having some trouble installing fonts into ubuntu. I believe that the fonts folder is in /usr/share/fonts/ but when i tried to put any fonts in there it said access denied.
Is there any other way to install font into ubuntu ?

Screenshot is in the attachment.

---

### Post by howefield on 2009-12-27
You'll need to open nautilus with gksudo to move files into that folder

```
gksudo nautilus
```

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by trintin7 on 2009-12-27
Thanks a lot finally I got to install fonts.

---

### Post by gradinaruvasile on 2009-12-27
Easier is to make a folder called .fonts (its a dot, not typo) in your home folder and copy your font files there. No root access required.

---

