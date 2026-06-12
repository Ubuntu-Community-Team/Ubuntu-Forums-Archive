---
title: "Files (Nautilus) font color ubuntu 13.10"
date: 2014-02-19
forum: Desktop Environments
---

### Post by adrhc on 2014-02-19
Hi, I have Ubuntu 13.10 (Unity desktop) and I'm really not happy with the font color for "Files" application: it's simply too gray for me. 
What should I do to make it black ?

PS: I understand that the "Files" application is in fact Nautilus but I don't know how to configure it

---

### Post by adrhc on 2014-02-20
I manage to find the answer:
one should edit /usr/share/themes/Ambiance/gtk-3.0/gtk-main.css

/*default color scheme */
@define-color bg_color #f2f1f0;
[COLOR=#0000ff]@define-color fg_color #000000;[/COLOR]
@define-color base_color #ffffff;
[COLOR=#0000ff]@define-color text_color #000000;[/COLOR]
@define-color selected_bg_color #f07746;
@define-color selected_fg_color #ffffff;
@define-color tooltip_bg_color #000000;
@define-color tooltip_fg_color #ffffff;

---

