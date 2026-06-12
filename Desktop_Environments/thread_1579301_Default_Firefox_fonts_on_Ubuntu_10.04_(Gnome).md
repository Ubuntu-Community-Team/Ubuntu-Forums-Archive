---
title: "Default Firefox fonts on Ubuntu 10.04 (Gnome)"
date: 2010-09-21
forum: Desktop Environments
---

### Post by Coderoid on 2010-09-21
Hi folks,

I'm running Ubuntu 10.04 (Gnome desktop) and always liked the default Firefox font. Today, I decided to install KDE and to give it a spin. Wll, my Gnome Firefox now uses the KDE font. What is the default font for Firefox on Gnome (10.04) and how can I get it back?

Thanks.

---

### Post by lovinglinux on 2010-09-21
Rename  or delete the file .fonts.conf in your home directory like this:

```
mv ~/.fonts.conf ~/.fonts.conf.bak
```

---

### Post by mikewhatever on 2010-09-21
If Gnome is still installed, you can check yourself in Firefox's preferences, content. I believe the default font is serif, but I don't have Lucid installed.

---

