---
title: "making kde default wm?"
date: 2005-08-31
forum: Desktop Environments
---

### Post by gr83 on 2005-08-31
Just did apt-get install kubuntu-desktop and works fine. However when creating a new user and logging in at KDM, the default windows manager become Gnome. I'd like to make KDE the default WM for any future users. Thanks in advance.

---

### Post by tonysathre on 2005-08-31
when u log with a different wm than the default it should prompt you if you want to make what ever your logging into the default wm

---

### Post by gr83 on 2005-08-31
[QUOTE=tonysathre]when u log with a different wm than the default it should prompt you if you want to make what ever your logging into the default wm[/QUOTE]
wish it was that simple but it does not ask. know of a file to edit?

---

### Post by tonysathre on 2005-08-31
edit /etc/X11/window-managers
after the commented lines (beginning with #), it lists, in order of
preference, windows managers to load, you want yours to be the first on
that list.

---

### Post by gr83 on 2005-08-31
theres no /etc/X11/window-managers file. if you posted an example followed by me customizing for my needs should it do the trick?

---

### Post by gnutux on 2005-09-01
run pkg-config xorg as root

gnutux

---

### Post by gr83 on 2005-09-01
[QUOTE=gnutux]run pkg-config xorg as root

gnutux[/QUOTE]
pkg-config xorg does nothing  :???:

---

