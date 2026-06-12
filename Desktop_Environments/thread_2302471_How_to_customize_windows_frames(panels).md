---
title: "How to customize windows frames(panels)"
date: 2015-11-10
forum: Desktop Environments
---

### Post by Veliko on 2015-11-10
[COLOR=#111111][FONT=Ubuntu]I want to learn to customize GTK themes. So far I have managed to learn how to change the background(accent) color, text color etc..[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I can change colors by changing the values in the files in /usr/share/themes//gtk-3.0/gtk.css. By changing values in this code I can play with the colors.[/FONT][/COLOR]
/* default color scheme */

@define-color bg_color #cdc3b8;
@define-color fg_color #262626;
@define-color base_color #accdff;
@define-color text_color #262626;
@define-color selected_bg_color #01b9fc;
@define-color selected_fg_color #ffffff;
@define-color tooltip_bg_color #A3D0FF;
@define-color tooltip_fg_color #023C79;
[COLOR=#111111][FONT=Ubuntu]But where exactly in the theme are the files for the windows frames(panels) so I can change text of the tittlebar, change color of the frames ? If possible would really be helpful if you also say what code is for what purpose.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thank you.[/FONT][/COLOR]

---

### Post by vasa1 on 2015-11-11
> **Veliko said:**
>  ...But where exactly in the theme are the files for the windows frames(panels) so I can change text of the tittlebar, change color of the frames ? If possible would really be helpful if you also say what code is for what purpose. ...

"Window frames" aren't the same as panels. AFAIK, gtk themes don't control the appearance of "window frames".

You need to tell people which window manager you're using.

You need to tell people which panel you're using.

---

