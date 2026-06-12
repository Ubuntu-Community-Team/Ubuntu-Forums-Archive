---
title: "removing programs installed with wine"
date: 2009-05-19
forum: General Help
---

### Post by fminmexico on 2009-05-19
I have used the uninstaller on the windows program,removed what was left in C programs but I still have all the shorcuts and programs showing in the Other menu..A right click delete does not work.How do I delete them.
     fminmexico.

---

### Post by michy99 on 2009-05-19
Delete them from /home/{YOUR_USERNAME}/.local/share/applications/wine/programs.

Note that .local is a hidden folder, so you may have to crtl+h to see it in nautilus.

---

### Post by fminmexico on 2009-05-21
> **michy99 said:**
> Delete them from /home/{YOUR_USERNAME}/.local/share/applications/wine/programs.

Note that .local is a hidden folder, so you may have to crtl+h to see it in nautilus.

 When I showed the hidden folders there was no local/share/applications/wine/programs.there was a wine folder but it had no references to the shortcuts that I want to delete.
  fminmexico.

---

### Post by coffeecat on 2009-05-21
> **michy99 said:**
> Delete them from /home/{YOUR_USERNAME}/.local/share/applications/wine/programs.

Note that .local is a hidden folder, so you may have to crtl+h to see it in nautilus.

Thanks for that - it worked fine to get some uninstalled hangers-on in my wine programs menu.

**fminmexico**, ~/.local/share/applications/wine/programs is in my system. It's '.local', not 'local'.

**Edit:** - just noticed you've tagged this thread xubuntu, so you're using xfce. Perhaps it's different in xfce. ~/.local/share/ is there in gnome.

---

### Post by fminmexico on 2009-05-21
> **coffeecat said:**
> Thanks for that - it worked fine to get some uninstalled hangers-on in my wine programs menu.

**fminmexico**, ~/.local/share/applications/wine/programs is in my system. It's '.local', not 'local'.

**Edit:** - just noticed you've tagged this thread xubuntu, so you're using xfce. Perhaps it's different in xfce. ~/.local/share/ is there in gnome.

I really could not tell you.
 fminmexico.

---

