---
title: "Installing new themes for Edgy"
date: 2007-02-14
forum: Desktop Environments
---

### Post by acerlinux on 2007-02-14
I downloaded some themes from gnome-look, but no matter what themes I installed, they are all look the same and ugly except the theme's name is different. Does some one know the reason? Your help will be grateful.

I am using ubuntu edgy with beryl svn builds.

---

### Post by acerlinux on 2007-02-15
sorry for bringing this up, cause really need help with it. Thanks in advanced.

---

### Post by mcduck on 2007-02-15
Do you have the GTK2-engines that those themes use installed?

At least get the 'gtk2-engies-pixbuf'-package (you may need to enable Universe repository if you haven't done that already).

Oh, and one more thing (as you are using Beryl): try running 'gnome-settings-daemon &' from a terminal and if that fixes your problem add 'gnome-settings-daemon' to your session startup in System/Preferences/Session.

---

### Post by acerlinux on 2007-02-15
I already have the 'gtk2-engines' package installed, do you think I still need 'gtk2-engies-pixbuf'?

Any way, really thanks for your answers. I will try any possible solutions.

---

### Post by acerlinux on 2007-02-15
simply installed the 'gtk2-engines-pixbuf' and the problem solved, thanks very much

---

