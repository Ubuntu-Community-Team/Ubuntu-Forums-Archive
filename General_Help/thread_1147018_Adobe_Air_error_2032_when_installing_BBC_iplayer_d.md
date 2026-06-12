---
title: "Adobe Air error 2032 when installing BBC iplayer desktop"
date: 2009-05-03
forum: General Help
---

### Post by ajhunt on 2009-05-03
Hi all!

Air is giving an error 2032 when installing iplayer desktop on my 64 bit ubuntu. The BBC website suggests a firewall problem but I'm not running one so has anyone else had the problem / got this working?

Many thanks.

---

### Post by ajhunt on 2009-05-03
Some progress by:

sudo cp /usr/lib/libadobecertstore.so /usr/lib32

Iplayer Desktop then installs OK. However nothing happens when trying to use it. If I launch it in a terminal, I get the following error:

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

I'll keep looking for the solution!

---

