---
title: "Panel with side orientation color errors"
date: 2010-02-09
forum: Desktop Environments
---

### Post by thirtysixbelow on 2010-02-09
I like to have my panel containing the menus, system icons, and logout menu with right side orientation. When I move it to the right the color sections get all out of whack. Anyone have an idea how to resolve this? I tried changing the background color of the panel and it only changed a subsection of the panel which was still oriented improperly.

---

### Post by mcduck on 2010-02-09
Nothing wrong with the colors, it's just that the background image you are using (or your GTK theme has defined) for your panel isn't rotated with the panel.

Tbe thing here is that gnome-panel is actually able to rotate (and scale) panel backgrounds correctly for vertical panels. Btut you need to enable that yourself in gconf-editor, and it doesn't work for panel backgrounds that come from your GTK theme, only for background images you have set yourself directly from the panel's options.

What you'll need to do is to edit the GTK theme you use and remove the panel backgrond from it. Then set the background image you want to use in the panel's options, and finally run gconf-editor, browse to apps/panel/toplevels/*your panel's name here*/background and enable the "rotate"-key.

And yes, sorry about the "edit your GTKL theme"-part. :) This is why I really dislike it when GTK themes include panel theming. It just doesn't work for any other than the default panel setup, and for anyhting else you need to manally remove it from the theme. Providing the panel background as separate image file that everybody could add to their panel if they want to wouldn't make installing themes that much harder and would solve most of panel background -related problems.n (or then Gnome could just make the rotate and scale-options work eith GTK thems as well, and enable them by default..But I dount they'd do that, considering that the options themselves are hidden in gconf only and not in panel's options..)

---

