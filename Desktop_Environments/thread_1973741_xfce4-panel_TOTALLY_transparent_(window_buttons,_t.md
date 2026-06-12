---
title: "xfce4-panel TOTALLY transparent??? (window buttons, too) (customize via ~/.gtkrc-2.0)"
date: 2012-05-05
forum: Desktop Environments
---

### Post by ohnonot on 2012-05-05
hello,
i just spent 2 hours searching for documentation on this...
:-(

right now i have a transparent panel background, but the window buttons still have an opaque background when focused. i'd like them to be TOTALLY transparent all the time. 
i guess there must be a way of adding some lines to gtkrc-2.0 that achieve that.

also, if someone knows where to find documentation on this - how gtk is being used in xfce, particularly the panel. all i found is [-this-]("http://docs.xfce.org/xfce/xfce4-panel/theming").

thanks.
.
.
.

---

### Post by zombifier25 on 2012-05-05
[This tutorial solves the same problem in GNOME, I don't know if it will work with XFCE considering the fact that both of them uses gtkrc-2.0.](http://www.howtogeek.com/howto/43673/how-to-make-the-gnome-panels-in-ubuntu-totally-transparent/)

---

### Post by Toz on 2012-05-05
If you're using xfce 4.8, then in the Window Buttons properties, check off "Show Flat Buttons".

---

### Post by Jose Catre-Vandis on 2012-05-05
> **Toz said:**
> If you're using xfce 4.8, then in the Window Buttons properties, check off "Show Flat Buttons".

Where ?  Can't find that

---

### Post by Toz on 2012-05-05
Try: Settings Manager -> Panel -> Select the correct panel -> Items tab -> Window Buttons -> Edit button.

---

### Post by Jose Catre-Vandis on 2012-05-05
Ah - the panel has to have "Window Buttons" on it, I looked at one of my panels without this, hence I couldn't find it. ;)

---

### Post by brainwash on 2012-05-05
You should be able to set a transparent background for all window buttons (regardless of state) by using the pixmap theme engine. First, check if the package **gtk2-engines-pixbuf** is already installed on your system. Then visit this website:

[http://live.gnome.org/GnomeArt/Tutorials/GtkEngines/PixmapEngine](http://live.gnome.org/GnomeArt/Tutorials/GtkEngines/PixmapEngine)

Use GIMP to create the needed transparent png/xpm file(s). :)

---

### Post by ohnonot on 2012-05-06
[thanx toz, flat buttons helps but not 100%]

thanks brainwash, that was a nudge in the right direction!

i found a theme that's using pixmap and copied the relevant part (the theme has a separate panel.rc) into some already existing xfce-panel customizations in ~/.gtkrc-2.0.
plus, i copied the folder with the Panel pixmaps/png's into my homefolder and made all the png's totally transparent (that was just a job of copying & renaming one that already was transparent).

this added to ~/.gtkrc-2.0:```
style "xfcepanel"
{
xthickness = 0 # from here until "Modd 10" is not relevant for this forum thread...
ythickness = 0
GtkButton::inner-border = {3,1,1,1}
#XfcePanelWindow::autohide-size = 1
font_name = "Modd 10" # ...but i left it here to show how these things work.
engine "pixmap" {
        image {
            function    = BOX
            recolorable    = TRUE
            state        = NORMAL
            }
        image {
            function    = BOX
            recolorable    = TRUE
            state        = PRELIGHT
            file        = "Panel/panel-button-hover.png"
            border        = { 3, 1, 1, 1 }
            stretch        = TRUE
            }
        image {
            function    = BOX
            recolorable    = TRUE
            state        = ACTIVE
            file        = "Panel/panel-button-active.png"
            border        = { 3, 1, 1, 1 }
            stretch        = TRUE
            }
        image {
            function    = BOX
            recolorable    = TRUE
            state        = SELECTED
            file        = "Panel/panel-button-active.png"
            border        = { 3, 1, 1, 1 }
            stretch        = TRUE
            }
        image {
            function    = BOX
            recolorable    = TRUE
            state        = INSENSITIVE
            }
        image {
            function    = ARROW
            recolorable    = TRUE
            arrow_direction    = DOWN
            }
        }
}
widget_class "XfcePanelWindow*" style "xfcepanel"

```and the window buttons are totally transparent, it's just the letters. for all themes. but the colors of the letters change according to the theme.
:guitar:solved!
see it [here.]("http://dasbaer.deviantart.com/art/creamy-chocolate-moon-tied-tickled-298137314")

---

