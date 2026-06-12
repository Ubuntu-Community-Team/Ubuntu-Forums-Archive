---
title: "How to disable mouseover text?"
date: 2010-12-16
forum: Desktop Environments
---

### Post by Osedax on 2010-12-16
So, in Gnome, whenever you put the cursor over certain items on a panel, or menu, or whatever, a little box pops up next to the cursor with text saying the same thing as what you're about to click on. This feature is useless and highly annoying, but I can find no way of disabling it. How can I make it go away? And how can I do the same in applications like Firefox, if these are separate?

---

### Post by Osedax on 2010-12-16
[[COLOR="RoyalBlue"]Bingo.[/COLOR]]("http://forums.scotsnewsletter.com/index.php?showtopic=36880") Turns out these things are called "tooltips". Funny how Google is only useful if you know what you're looking for. Unfortunately, there doesn't seem to be a completely universal method of getting rid of them, only piecemeal, per-application fixes.

---

### Post by jimingkui on 2010-12-17
To disable mouseover text boxes in gnome panel/menu

1. Press Alt+F2, run **gconf-editor**
2. navigate to **apps/panel/global/**, and uncheck "tooltips_enabled" in right.

---

