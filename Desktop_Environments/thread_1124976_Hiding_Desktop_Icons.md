---
title: "Hiding Desktop Icons"
date: 2009-04-13
forum: Desktop Environments
---

### Post by TheIdiotThatIsMe on 2009-04-13
Howdy! Is it possible to hide the icons that appear on the Gnome desktop? For example, whenever I mount my Windows partition, it shows an icon on the desktop. Is there way to turn that off, so it doesn't show up on the desktop?

---

### Post by crossedout on 2009-04-14
Open configuration editor (gconf-editor in terminal), navigate to apps->nautilus->desktop and uncheck the 'volumes visible' selection.  That should do it for you.

-Xout

---

### Post by TheIdiotThatIsMe on 2009-04-14
Thanks a ton!

---

