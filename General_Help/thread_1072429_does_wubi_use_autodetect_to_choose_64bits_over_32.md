---
title: "does wubi use autodetect to choose 64bits over 32?"
date: 2009-02-17
forum: General Help
---

### Post by BUGabundo on 2009-02-17
I was trying to install ubuntu with wubi over vista, on a friends laptop, and wubi ended up installing the 64 bits version (maybe because he has 4GiBs of RAM).
but some bug related to the laptop being SIS based, gives probs with network and acpi.


is there a way to make wubi install 32 bits?

---

### Post by sdennie on 2009-02-17
There isn't enough room on the CD to hold both 32bit and 64bit packages so, I would guess that the reason it installed 64bit is because you downloaded the 64bit ISO.  You could verify this by booting from the CD and, once the live CD environment comes up, typing:

```

uname -m

```

If it doesn't say, "i686" it means you downloaded the 64bit version instead of the 32bit version.

---

### Post by BUGabundo on 2009-02-17
thanks for the quick reply. I'm an experienced user on Ubuntu, just not on wubi.
I did not download any image, wubi did.
But from reading a bit more, i can force it using --32bits command

---

