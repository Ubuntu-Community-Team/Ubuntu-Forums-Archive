---
title: "Icons for installed non-Ubuntu applications"
date: 2005-02-12
forum: Desktop Environments
---

### Post by chryz on 2005-02-12
I noticed during the installation of Debian-packages (from universe I think it's called) that icons were created for the newly installed applications end up in "/usr/lib/menu", but these aren't included in the Ubuntu desktop.

I noticed that both these files and the ones used on the Ubuntu desktop are plain textfiles and based on the information they hold it should be a small matter mapping the contents from one format to the other. Any obvious tool or hint regarding this I haven't noticed - I'm new to the whole Linux-with-GUI thingie so that would explain any glaring oversights in this regard.

---

### Post by tim1 on 2005-02-12
The files in /usr/lib/menu are the debian menu files. The entries shown in the Gnome menu of ubuntu rely on .desktop files in /usr/share/applications. The latter are a freedesktop.org specification, currently supported at least by gnome, xfce & kde, and myabe others, and are preffered over the debian menu files. If an application is missing a menu entry, you should file a bug I think.

greets, tim

---

### Post by drasko on 2005-02-12
Check out directory /usr/share/gnome/Apps. KDE application lounchers are stored in /usr/ahre/applications, as mentioned above, but if some of your kde applications cannot be seen from gmome meny try copying them from here (they have .desktop extension) to /usr/share/gnome/Apps. Now they should be visibele in Gnome meni.
...or you can add these manually from th meni - right click.

Drasko

---

