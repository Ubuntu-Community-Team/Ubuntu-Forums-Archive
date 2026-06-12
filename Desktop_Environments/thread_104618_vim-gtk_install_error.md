---
title: "vim-gtk install error"
date: 2005-12-16
forum: Desktop Environments
---

### Post by pksings on 2005-12-16
dpkg-divert: `diversion of /usr/bin/vim to /usr/bin/vim.org by vim-gtk' clashes with `diversion of /usr/bin/vim to /usr/bin/vim.org by vim-gnome'
dpkg: error processing /var/cache/apt/archives/vim-gtk_1%3a6.3-078+1ubuntu3_i386.deb (--unpack):

Ubuntu Breezy, doing a KDE install started this. But the error above is from "apt-get install vim-gtk".  I did that after the KDE install failed with this file and error.

PK

--------------------------------------------------------------------------------------------
(update-solved)


I solved this by going to init 1. Then re-installing vim-gnome. apt-get install vim-gnome, it then proceeded to finish the rest of the KDE install automatically.  

I believe this is a minor bug in the KDE install, instead of attempting to install the vim-gtk package perhaps the vim-gnome one should be used. In my case I already had vim-gnome in place as I am switching from Gnome to KDE and they obviously do not co-exist peacefully as both are doing redirects and only the first one is allowed to do so and the second one, in my case vim-gtk, fails and the entire install aborts.

PK

---

### Post by robotgeek on 2005-12-16
[QUOTE=pksings]dpkg-divert: `diversion of /usr/bin/vim to /usr/bin/vim.org by vim-gtk' clashes with `diversion of /usr/bin/vim to /usr/bin/vim.org by vim-gnome'
dpkg: error processing /var/cache/apt/archives/vim-gtk_1%3a6.3-078+1ubuntu3_i386.deb (--unpack):


Ubuntu Breezy, doing a KDE install started this. But the error above is from "apt-get install vim-gtk".  I did that after the KDE install failed with this file and error.[/QUOTE]

try "sudo apt-get dist-upgrade"

---

