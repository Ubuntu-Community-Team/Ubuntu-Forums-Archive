---
title: "Well hello Debian..."
date: 2005-05-13
forum: Desktop Environments
---

### Post by BAshworth on 2005-05-13
I suddenly have a Debian sub-menu in my regular gnome menu. (complete with Debian icon and everything) No idea exactly when it came to be, but I noticed it after installing k3b.

When I hover over it, it expands out to be an almost exact copy of the entire regular menu.

Any ideas to what could have caused this? (and how to get rid of it?)

---

### Post by bored2k on 2005-05-13
Getting rid of it :
sudo apt-get remove --purge menu -y
sudo apt-get remove --purge menu-xdg -y

KDE dependencies probably installed it (k3b's).

---

### Post by BAshworth on 2005-05-14
[QUOTE=bored2k]KDE dependencies probably installed it (k3b's).[/QUOTE]

Makes sense.  Thanks.

---

