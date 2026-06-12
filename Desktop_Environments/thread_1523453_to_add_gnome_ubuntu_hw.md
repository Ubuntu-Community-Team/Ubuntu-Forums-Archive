---
title: "to add gnome ubuntu hw?"
date: 2010-07-03
forum: Desktop Environments
---

### Post by ottosykora on 2010-07-03
On an old laptop I was forced to use xubuntu earlier, since ubuntu from 8.04 and up did not work with the graphic card.

The ubuntu 10.04 does work well on it, tested with life CD.

Updated now the xubuntu to version 10.04 too, all works so far. Now I would like to add the gnome desktop, or simply change all to standard ubuntu 10.04 now.

What do I have to install now so I have the full ubuntu gnome ready?

( in synaptic, there are many , many files, but which are essential and which not?)

---

### Post by SmokeyThePanda on 2010-07-03
It is my understanding that if you wish to switch over to ubuntu, you would use the following commands:

[I]sudo apt-get install ubuntu-desktop

[/I]After that installs, you would then use the following command to remove xubuntu:

[I]sudo apt-get remove -purge xubuntu-desktop

[/I]I would personally stick with xubuntu, though to each his own. The packages may be named differently and if that is so, you can check your synaptic for the proper packages. However, those are close.

---

### Post by SmokeyThePanda on 2010-07-03
Just a note, if you wish to simply add the gnome window manager and keep your xubuntu, you can use the following command:

*sudo apt-get install gnome-core*

---

