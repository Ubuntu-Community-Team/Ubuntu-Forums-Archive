---
title: "Gnome 14.04 topbar!!!!"
date: 2015-05-07
forum: Desktop Environments
---

### Post by Karl_Hungus on 2015-05-07
that damn top bar! I cant figure out how get it hide with GNOME SHELL 3.10.4 PLEASE HELP! I found a bunch of SUPER OLD extensions that claim to do the what I am trying to accomplish but fail.

anyway If anyone could help I would really appreciate it!

---

### Post by buzzingrobot on 2015-05-07
You've looked at extensions.gnome.org, right?

Extensions are often sensitive to changes from one Gnome release to another.  Sometimes, though, an extension will work if its 'metadata.json' file is edited to add the specific Gnome version you're using. Extensions live in directories in .local/share/gnome-shell/extensions in your home directory. The list of shell versions is obvious inside metadata.json.   After the edit, do an alt-f2+r or logout so Gnome picks up the change.

---

### Post by Karl_Hungus on 2015-05-07
thanks for pointing me in the right direction! that's awesome

---

