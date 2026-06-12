---
title: "Font size problems"
date: 2005-09-08
forum: Desktop Environments
---

### Post by ddubuntu on 2005-09-08
Some applications (Gtktalog, Audacity, maybe others...) in Kubuntu display big characters... All fonts size in KDE applications are ok, and fonts size in gnome seems ok too.
Note that I have configured KDE fonts and Gnome fonts with KDE and Gnome configuration centers.
Thanks for all your advices.

David.

---

### Post by jrcmuniz on 2005-09-08
[QUOTE=ddubuntu]Some applications (Gtktalog, Audacity, maybe others...) in Kubuntu display big characters... All fonts size in KDE applications are ok, and fonts size in gnome seems ok too.
Note that I have configured KDE fonts and Gnome fonts with KDE and Gnome configuration centers.
Thanks for all your advices.

David.[/QUOTE]

I have the SAME problem!!!

Please... any help?!!

thanks!

---

### Post by Hobbsee on 2005-09-09
[QUOTE=jrcmuniz]I have the SAME problem!!!

Please... any help?!!

thanks![/QUOTE]
 Try installing gtk2-engines-gtk-qt

> sudo apt-get install gtk2-engines-gtk-qt

Then in control centre (kcontrol), force the gnome apps to use the kde fonts, and it looks way better :D

That should fix your problem - all my gnome fonts were too small in kubuntu, and that fixed it.

It's in universe, so you'll need the extra repositories from the ubuntuguide...

---

### Post by jeffjanzen on 2005-11-22
i'm having the same problem in ubuntu.  can i fix it without kcontrol?

---

