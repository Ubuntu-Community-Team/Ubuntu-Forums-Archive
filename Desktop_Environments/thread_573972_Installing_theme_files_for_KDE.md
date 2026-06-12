---
title: "Installing theme files for KDE"
date: 2007-10-12
forum: Desktop Environments
---

### Post by PmDematagoda on 2007-10-12
I have a problem when I try to compile the theme and styles I get from the internet, this is what I get:-

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

How do I fix this?

---

### Post by mexlinux on 2007-10-12
You need qt and/or kde dev packages
the error should say something in it's complete output

---

### Post by PmDematagoda on 2007-10-12
I believe I am missing the KDE dev packages, can you give me the name of that package/s so I can install through apt-get?

---

### Post by mexlinux on 2007-10-13
kdebase-dev should help

---

