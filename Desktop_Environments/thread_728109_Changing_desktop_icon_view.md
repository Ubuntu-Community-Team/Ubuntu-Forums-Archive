---
title: "Changing desktop icon view"
date: 2008-03-18
forum: Desktop Environments
---

### Post by betawind on 2008-03-18
On my Windows systems I have a great little application called DeskView that changes my desktop icons to look like what you see below (small icons with the text to the right, similar to List View in a file browser).  I was wondering if anyone knew a way to accomplish this in Linux (KDE or GNOME).

Thanks in advance,

Beta

[IMG]http://img159.imageshack.us/img159/1175/iconskw1.jpg[/IMG]

---

### Post by deepclutch on 2008-03-18
it may be possible.well in Gnome ,may be gconf got some options in nautilus for this!
OK!found !:
how :
open gconf-editor(run it by pressing ALT+F2 to get run dialog,inside run gconf-editor)
browse to apps>nautilus>icon_view>labels_beside_icons =>[COLOR=Red]**Tick**[/COLOR] it!
now open a terminal and do:
```
sudo killall  nautilus
```now everything will be besides icon :) Hope it helps!

---

### Post by betawind on 2008-03-18
Thanks for the suggestion deepclutch, but that only seems to affect actual nautilus windows, not the actual desktop.  Just for grins I tried adding the same key to the desktop portion of nautilus with no luck.  Any other thought?

---

### Post by takmsdsm on 2008-04-08
I LOVE desktoplistview for windows. I am surprised there isnt anything like this for linux with it being as customizable as it is. Hope someone makes a comparable tweak that does the same for us.

---

