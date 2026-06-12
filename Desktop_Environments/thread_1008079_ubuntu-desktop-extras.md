---
title: "ubuntu-desktop-extras?"
date: 2008-12-11
forum: Desktop Environments
---

### Post by suffice on 2008-12-11
Hi...

I had some problems with my system...I had to reinstall, and the only cd i had was mythbuntu 8.10....which installs xfce by default and a limited amout of extras....

i then installed 'ubuntu-desktop' to get back to my regular gnome, but it didnt install the bunch of extras like pidgin, openoffice, movie player yada yada...which generally dont really care about, but its also missingl like 'gnome-mount-extensions'...

if i remember correctly i need to install a package called something like 'ubuntu-desktop-extras' but i cant remember the exact name of it...any ideas?

---

### Post by jastonas on 2008-12-11
i dont think there is such a package.. why dont you install invidually the ones you need?

---

### Post by warbread on 2008-12-11
Do a keyword search in synaptic to get everything you want.  Or, reinstall using an Ubuntu cd.

---

### Post by ugm6hr on 2008-12-11
Try aptitude --with-recommends:

```
sudo aptitude install -r ubuntu-desktop
```

-r is equivalent to --with-recommends

---

### Post by suffice on 2008-12-11
cool...thanks guys....i just basically reinstalled from scratch again....all is good now

---

