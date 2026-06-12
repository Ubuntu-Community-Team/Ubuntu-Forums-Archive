---
title: "Auto hide GNOME panel too big"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by lhabjane on 2007-06-23
When I enable auto hide for my GNOME panel, it's still visible a few pixels (I can see part of the icons in the panel) and that looks terrible.. Can I make it hide more? Just see a thin line on the bottom?

---

### Post by jpeddicord on 2007-06-25
Yep, there is a hidden configuration option for this. Press Alt+F2 (or open a terminal) and type "gconf-editor".

In there, navigate through the tree to /apps/panel/toplevels/. Inside that category you will find bottom_panel_screen0 and top_panel_screen0 (the names may vary).

With one of the panel categories highlighted: In the right pane, there should be an option near the top labeled "auto_hide_size", and it is probably set to 6. Change the value to something smaller, maybe 1 or 2. Do not make it 0 however; this will hide your panel and not let you show it again.

Do the same thing for the other panel categories if you want to change their sizes also. The changes will be instant. When you are done, simply close the editor.

Jacob

---

### Post by lhabjane on 2007-07-03
Thank you very much! Sorry for late reply but you saved me alot of time!

---

