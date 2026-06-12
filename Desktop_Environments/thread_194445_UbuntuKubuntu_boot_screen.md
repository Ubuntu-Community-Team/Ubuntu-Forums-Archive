---
title: "Ubuntu/Kubuntu boot screen"
date: 2006-06-11
forum: Desktop Environments
---

### Post by stinerman on 2006-06-11
Gentlemen (and Ladies),

Is there a way to change the boot screen logo during boot-up?  I wanted to try Kubuntu and the logo has been Kubuntu even after I uninstalled most of it.  I'd like to get it back to the orange Ubuntu logo or, perhaps use a custom logo.

Thanks in advance.

---

### Post by Ramses de Norre on 2006-06-11
```
sudo update-alternatives --config usplash-artwork.so
```

It's possible to make a custom one but I don't know how.

---

### Post by stinerman on 2006-06-11
Perfect!

Thanks.

---

### Post by Fafnir on 2006-06-11
Actually, how *would* you make a custom one? I think the file that needs to be changed is /usr/lib/usplash/usplash-artwork.so, but it doesn't seem to be an image file - I am confused...

Thanks in advance!

---

### Post by stinerman on 2006-06-11
Its a .so (shared library), so there must be something during compilation that pulls in an image file and puts it in the startup routine.

Since the OS hasn't really loaded anything at that time, it would probably be hard to load any type of file short of a bitmap image to put in the screen.

---

