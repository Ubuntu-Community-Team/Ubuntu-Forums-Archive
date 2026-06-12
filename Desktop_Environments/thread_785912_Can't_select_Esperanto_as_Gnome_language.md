---
title: "Can't select Esperanto as Gnome language"
date: 2008-05-07
forum: Desktop Environments
---

### Post by Soldeace on 2008-05-07
In GDM it's not possible to select Esperanto as the environment language, although all packs related to Esperanto are properly installed.

The bug was mentioned here:
[https://launchpad.net/ubuntu/+source/langpack-locales/+bug/23435](https://launchpad.net/ubuntu/+source/langpack-locales/+bug/23435)

I tried a " export LANG=eo_XX " (and eo_XX.UTF-8) after editing  /etc/gdm/locale.conf and still no success.


Any idea?

---

### Post by advoss on 2008-10-06
The command ```
sudo localedef -f UTF-8 -i eo eo.UTF-8
``` (suggested on the bug page) fixed it for me

---

