---
title: "Firefox menu fonts in GNOME"
date: 2007-07-13
forum: Desktop Environments
---

### Post by Death &amp; Taxes on 2007-07-13
I installed a new hard drive today and reinstalled Ubuntu, and everything works fine, except that for some odd reason Firefox uses a different font for menus, toolbars, dialog boxes etc. than GNOME. The fonts are set to Verdana in the GNOME font panel, but Firefox sticks to sans-serif. You can see the difference here:

[IMG]http://img466.imageshack.us/img466/3251/firefoxfontxk5.jpg[/IMG]

It never did that before (it always automatically set the same font GNOME used). I changed all available font options in userChrome.css (that is all that I'm aware of) to Verdana, but that didn't do the trick either:

```
* {
font-family: "Verdana" !important;
font-size: 10pt !important;
}

menubar, menubutton, menulist, menu, menuitem {
  font-family: "Verdana" !important;
  font-size: 10pt !important;
}

window {
  font-size: 10pt !important;
  font-family: "Verdana" !important;
}
```

The font rendering of HTML looks fine though, so this is just an issue of the application itself. Anything I might have overlooked? How do I force Firefox to use the same font settings?

Versions:
Firefox 2.0.0.4
GNOME 2.18.1
Ubuntu 7.04

Thanks for any help.

---

### Post by nyex on 2007-09-23
I'm having the same issue. and I want bitstream vera. does anyone have any clue?

---

### Post by cvaty on 2007-10-03
ditto on the issue.., anyone have a solution?

---

### Post by defcomexperiment on 2007-10-03
you may be able to change it in the configuration of firefox to access it put about:config in the address bar... here is a list of the configuration entrys and descriptions, i am not sure if it will help but you may should find a way to change what you need in there...

[http://kb.mozillazine.org/Firefox_:_FAQs_:_About:config_Entries](http://kb.mozillazine.org/Firefox_:_FAQs_:_About:config_Entries)

---

### Post by Arthur_Dent on 2007-10-03
about:config won't do anything useful. Try reading [http://kb.mozillazine.org/Pane_and_menu_fonts](http://kb.mozillazine.org/Pane_and_menu_fonts)

---

### Post by Armadillo Kilr on 2007-10-03
so you're saying you already tried setting a default font through the content tab in preferences and it still didn't work?

---

### Post by Arthur_Dent on 2007-10-03
The Edit => preferences => content options only apply to pages, not the UI.

---

