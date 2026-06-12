---
title: "Black borders on GTK2 app tooltips"
date: 2016-09-20
forum: Desktop Environments
---

### Post by amadis2009 on 2016-09-20
It seems that (some?, all?)Gtk2 apps show tooltips with black borders, no matter what theme I use. I can use Gnome Color Chooser, which allows me to set the background color and the font color, but there is no way to set border color or remove the border. Does anyone know how to do this. I'd really like tooltips to follow the rest of my theme.

---

### Post by vasa1 on 2016-09-20
Ubuntu version?
Theme name and version and source (if not from standard repos)?
gtk2 apps in question? You wrote "(some? all)": why the uncertainty?

---

### Post by amadis2009 on 2016-09-20
Soory, Ubuntu 16.04 (flashback session). Themes I've tried are Adwaita, Arc, Elegant Brit, and High Contrast. I can't tell if Ambiance and Radiance have the black borders because the whole tooltip background is black. Apps that I'm seeing this in are Deluge, Thunderbird, Audacity, and on non-csd titlebars (close, min, max buttons).

---

### Post by Frogs Hair on 2016-09-22
Even if using the flashback session you would need Gnome 3.18 themes for best results. I know Elegant Brit hasn't been updated for a very long time , but Arc 3.18 should work.
Are you using the Compiz or Metacity session.

---

### Post by amadis2009 on 2016-09-22
I'm using the Compiz session. I'm not actually using Elegant Brit anymore. I was just showing that I get these black borders on all of the themes I've tried. Arc included.

---

### Post by vasa1 on 2016-09-22
> **amadis2009 said:**
> I'm using the Compiz session. I'm not actually using Elegant Brit anymore. I was just showing that I get these black borders on all of the themes I've tried. Arc included.

Could you post the top part of the relevant gtkrc file? The theme I use has this, in part:```

gtk_color_scheme	= "bg_color:#404040\nselected_bg_color:#001B33\nbase_color:#222222" # Background, base.
gtk_color_scheme	= "fg_color:#000000\nselected_fg_color:#999999\ntext_color:#888888" # Foreground, text.
gtk_color_scheme	= "tooltip_bg_color:#333333\ntooltip_fg_color:#000010" # Tooltips. fg was #888888
gtk_color_scheme	= "link_color:#220808" # Hyperlinks
gtk_color_scheme	= "panel_bg:#686868" # Panel bg color
gtk_color_scheme	= "fm_color:#F7F7F7\ngrey:#aaaaaa\nred:red\nblue:blue\nwhite:white"
gtk_color_scheme	= "bg_color_dark:#686868\ntext_color_dark:#FFF"
```

The tooltips on gtk2 apps have black text on a grey background. If there is a black border, it isn't obvious enough to distract me.
I'll try to attach three images showing tooltips in geany, pcmanfm, and audacity.

---

### Post by amadis2009 on 2016-09-22
I'm going to have to leave for work very shortly so I'l have to post that info when I get back. But, I've been through the gtkrc files of all of these themes and can't find where the border or border color of tooltips is defined. In the pics you posted, your theme has grey tooltips, so of course you don't really notice the black border, but for themes that have a white tooltip or some other color, the border IS distracting as it doesn't match the rest of the theme. I'm just hoping someone can point me to where these borders are defined because it is not specific to any one particular theme.

---

### Post by vasa1 on 2016-09-22
Wildly guessing here, but maybe it has to do with the "engine" rather than each theme so that a color complementary to the tooltip background is chosen for the border. I've not come across any option to specify tooltip borders by editing gtkrc.

I briefly tried other background colors ... no black borders. The theme I'm using is Greybird which I've darkened considerably.

---

### Post by vasa1 on 2016-09-23
> **amadis2009 said:**
> ... In the pics you posted, your theme has grey tooltips, so of course you don't really notice the black border, but for themes that have a white tooltip or some other color, the border IS distracting as it doesn't match the rest of the theme. ...

Here are some images of the same apps I posted before but with white tooltip backgrounds. Still no black border.

---

### Post by amadis2009 on 2016-09-26
The engine guess was a good one. I was able to define the engine for tooltips with Gnome Color Chooser. The Glide and Murrine engines both remove the black borders, though there is a gray shadow around the frame. Glide seems to have the lightest shadow so the tooltips (for the most part) match the rest of my themes. Thanks for the help.

---

