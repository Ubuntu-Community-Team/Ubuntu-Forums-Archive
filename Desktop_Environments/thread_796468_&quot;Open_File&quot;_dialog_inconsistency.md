---
title: "&quot;Open File&quot; dialog inconsistency"
date: 2008-05-16
forum: Desktop Environments
---

### Post by dyefade on 2008-05-16
Hi, I'm having trouble with Samba shares in Hardy.

In bundled Gnome apps, such as Gedit or Rhythmbox, my SSH shares are listed in the "Places", column. In other (gtk) applications, such as Banshee and EasyTag, they are not.

Why is this?


Since I can no longer mount Samba shares properly, I'm now unable to access many of my files with certain applications.

---

### Post by jpietari on 2008-05-16
My best guess.

In 7.04 or 7.10 Gnome updated their File Dialog (GTK).  Maybe Banshee is still using the old File Dialog or since it is written using mono (.NET), it uses a different File Dialog.

---

