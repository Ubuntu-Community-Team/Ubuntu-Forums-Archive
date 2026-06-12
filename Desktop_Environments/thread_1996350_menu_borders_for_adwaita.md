---
title: "menu borders for adwaita"
date: 2012-06-04
forum: Desktop Environments
---

### Post by frank_n on 2012-06-04
Ubuntu 12.04, 64bit, Gnome Classic. 

Is there a way to tweak (gtk3) Adwaita and give it menu borders?

Please note that this question follows extensive googling, extensive trial and error:

(1) All links older than April 2012 are obsolete and useless.

(2) The files gtk-main.css and gtk-widgets.css do not exist any longer. They are now part of a binary file. The file gtkrc does exactly nothing.

---

### Post by apocalyptech on 2012-06-11
Hello - I ran into this myself today and was able to solve it by creating the file [FONT=Courier New]~/.config/gtk-3.0/gtk.css [/FONT]with the following contents:

```
.menu {
    border-style: solid;
    border: 1px solid @fg_color;
}
```If you use that file, note that it'll actually override the CSS for ANY theme you have set, not just Adwaita.  I know that there's a file path you could use to have it only override Adwaita, but once I got that working I didn't much feel like digging around more.  Obviously you can edit to suit.

FWIW, it seems that the reason Adwaita was coded without a menu border is that it relies on your window manager adding a drop shadow, instead.  If, like me (and frank_n apparently), your WM doesn't do that, this might be for you.

---

### Post by pelle.k on 2012-06-18
Thanks a bunch! The only thing left to fix is the contextual (right click) menus inside application windows...

---

