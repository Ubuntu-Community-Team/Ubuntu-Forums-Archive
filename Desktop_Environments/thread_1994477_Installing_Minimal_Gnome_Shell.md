---
title: "Installing Minimal Gnome Shell?"
date: 2012-06-02
forum: Desktop Environments
---

### Post by gf11221 on 2012-06-02
How can i install the gnome shell without any preinstalled packages or programs in Ubuntu Server 12.04? And does it come with a login manager? If not, any recommendations?

**Thanks in advance!**

---

### Post by wilee-nilee on 2012-06-02
> **gf11221 said:**
> How can i install the gnome shell without any preinstalled packages or programs in Ubuntu Server 12.04? And does it come with a login manager? If not, any recommendations?

**Thanks in advance!**

There is no minimal gnome shell per-say.

Installing a desktop on top of the severs sort of defeats the purpose as well, you might as well just have the regular install.

---

### Post by gf11221 on 2012-06-02
I mean minimal for gnome shell since i just need the DE and didn't want some other packages to be in the installation process that won't be used.

is gnome-core okay?

---

### Post by LarsKongo on 2012-06-02
*sudo apt-get --no-install-recommends install gnome-shell*

That will install everything that's required to run gnome-shell. (Except graphic drivers.) It will not install a login manager, any themes or icons.

---

