---
title: "How to remove gnome"
date: 2010-10-02
forum: Desktop Environments
---

### Post by Kingcheese26 on 2010-10-02
Hi. I installed kde in ubuntu recently. For a while i didn't need it because I'd been using gnome, but gnome seems to be broken (if I boot up in it, the panel just doesn't show up. I think removing gnome and reinstalling it would be the best solution, but how do I do that? I tried apt-get remove ubuntu-desktop, but it told me that it wasn't installed, so not removed. Did I just get the package name wrong, or what?

---

### Post by Spice Weasel on 2010-10-02
apt-get remove gnome*? Check the packages that it removes carefully to make sure it doesn't remove anything important or a package that you want to keep.

---

### Post by Kingcheese26 on 2010-10-03
That didn't work but apt-get purge liborbit2 did.

---

