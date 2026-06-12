---
title: "can't install .deb files"
date: 2009-04-17
forum: General Help
---

### Post by banana jama on 2009-04-17
i just upgraded to ubuntu 9.04 rc (im posting here because i don't know if its a software problem or an firefox problem) when i try to download and install a third party software (this case adobe, i've also had problems with lightscribe) i get this message
 > /tmp/AdbeRdr9.1.0-1_i386linux_enu.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences. 
anyone knows why or what i can to do solve this problem? is it a firefox issue or an 9.04 RC issue?

edit: i think it's a firefox problem when i just save the .deb files it opens and install it.

---

### Post by Tim Sharitt on 2009-04-17
It's probably due to the wrong (or no) program being associated with .deb files when opening with firefox. Try to save the file to disk then either double clicking to open with Gdebi or installing with

```
sudo dpkg -i /path/to/file.deb
```

---

