---
title: "kde only"
date: 2005-06-23
forum: Desktop Environments
---

### Post by tlaloczint on 2005-06-23
hi to all I was wondering if there is a way I can safely remove Gnome. I originaly started with Gnomebut since my wife likes kde better well you know the history... well there is a little problem here I try the add remove instalation applet but just hangs out and wont let me remove Gnome
so I was wondering if there is a way I can do it with out messing kde ?

---

### Post by SGC on 2005-06-23
- Open Synaptic and search for ubuntu-desktop and right-click on it and mark it for removal.

- In Synaptic search for **gnome** and mark all the installed packages (the ones with green square, click on S column to order them) for removal except  the following (They are needed for Firefox, Azureus, and some other packages):

gnome-keyring
gnome-mime-data
libgnome2-0
libgnome2-common
libgnomecanvas2-0
libgnomecanvas2-common
libgnome-keyring0
libgnomeui-0
libgnomeui-common
libgnomevfs2-0
libgnomevfs2-common

- Click the apply button

If one of you program are removed after this process, don't worry, since all the settings and the files for this program still exist, just install the program again with apt-get, kynaptic, or synaptic. The important thing is to choose **Mark for Removal** not **Mark for complete removal** when you remove the packages.

---

### Post by tlaloczint on 2005-06-24
thank you very much that help me a lot thanks again, this comunity rocks

---

