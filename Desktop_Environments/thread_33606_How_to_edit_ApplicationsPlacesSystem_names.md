---
title: "How to edit Applications/Places/System names?"
date: 2005-05-11
forum: Desktop Environments
---

### Post by bluemax on 2005-05-11
Is there an easy way to change the names of the Applications, Places, and System menus? I looked in the applications.menu file and apparently you can't do it there, and I also tried a menu editor but these don't allow you to change these either. Is there a way to do this without completely removing the menus and re-adding them all over again with a different name?

---

### Post by jcooper on 2005-05-12
"Applications", "Places" and "System" are hard coded names, so to edit them you'd need to edit the source for the appropriate part of the panel and recompile it yourself. There is no other way of changing them.

Remember that these are also internationalised, so any editing may also require changing the language sources for the panel.

---

