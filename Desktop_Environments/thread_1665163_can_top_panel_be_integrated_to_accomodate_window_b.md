---
title: "can top panel be integrated to accomodate window borders / buttons ?"
date: 2011-01-11
forum: Desktop Environments
---

### Post by rvchari on 2011-01-11
hi...
its an interesting question i m posting. can we port the window buttons on top panel (when in maximized mode) while using global menu applet ? it will be similar to using unity (sans the ugly left panel)
wonder if someone has given a thought on this...

---

### Post by stinkeye on 2011-01-12
[**_[COLOR="DarkRed"]http://www.webupd8.org/2010/12/window-applets-0210-released.html[/COLOR]_**]("http://www.webupd8.org/2010/12/window-applets-0210-released.html")

---

### Post by rvchari on 2011-01-12
i tried window button on top panel after installing from webupd8. the purpose was to integrate window button / title with top panel in maximize mode (as it happens in unity (netbook edition), which doesnt happen now.

any further tweaks necessary ?

---

### Post by rvchari on 2011-01-12
it will be an ideal effect where the window buttons appear in maximized window and window title bar disappears to be integrated to top panel and reappears when on restore mode....
i m not interested in wondow title as it shos up in global menu applet....

---

### Post by stinkeye on 2011-01-13
Right click on the applet and adjust preferences.

---

### Post by rvchari on 2011-01-13
thanks buddy...
now panel looks real cute, especially after i downloaded and installed WoW theme to match the WoW buttons available in the preferences list....

its time i mark this thread is SOLVED...

just one doubt... m unable to remove the ugly arrow button alongside the main menu icon in top panel... any clue ? so that the ugly arrow be removed keeping the basic theme emboss style intact ?

---

### Post by stinkeye on 2011-01-14
> **rvchari said:**
> just one doubt... m unable to remove the ugly arrow button alongside the main menu icon in top panel... any clue ? so that the ugly arrow be removed keeping the basic theme emboss style intact ?

```
gedit ~/.gtkrc-2.0
```

and add this too it
```
#the following removes the arrows from the panel
style "panel-arrow-remove"

{
engine "pixmap"
{
image
{
function = ARROW
recolorable = TRUE
overlay_file = "arrows/arrow-blank.png"
overlay_border = {2,2,2,2}
overlay_stretch = FALSE
arrow_direction = UP
}

image
{
function = ARROW
recolorable = TRUE
overlay_file = "arrows/arrow-blank.png"
overlay_border = {2,2,2,2}
overlay_stretch = FALSE
arrow_direction = DOWN
}
}
}

widget_class "*PanelToplevel*" style "panel-arrow-remove"
```

---

### Post by rvchari on 2011-01-15
i did that after i got a link of another thread. but it remains in some theme, vanishes in other and gets uglier in a few !!!

so i usually revert back if it gets uglier and try to change theme where it works...

the one u mentioned says i use gedit `/.gtkrc. i was doing this individually for the installed themes in its respective gtkrc. does ur method save the gtkrc to be emulated in all the themes i have or i have to do in all the themes seperately ?

---

### Post by stinkeye on 2011-01-15
As far as I know the **~/.gtkrc-2.0** file is like a master file that overrides
a themes settings but I'm not sure it works with all theme engines.

If you use gnome-color-chooser to change things it creates a file **~/.gtkrc-2.0-gnome-color-chooser**
and makes an entry in the ~/.gtkrc-2.0 to use that file.

eg my ~/.gtkrc-2.0 file
```
include ".gtkrc-2.0-gnome-color-chooser"
gtk-menu-popup-delay = 0
gtk-enable-tooltips = 0
```

---

