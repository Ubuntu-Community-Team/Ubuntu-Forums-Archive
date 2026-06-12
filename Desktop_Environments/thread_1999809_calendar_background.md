---
title: "calendar background"
date: 2012-06-08
forum: Desktop Environments
---

### Post by linuxonbute on 2012-06-08
I am running 12.04 with gnome 3 NOT unity. I like it and have only one annoying problem. The calendar is almost unusable as the the background and text are semi transparent and so the text on the drop down providing the full calendar cannot be viewed.
is there a config file or some other way I can tweak this?

---

### Post by Frogs Hair on 2012-06-08
You change the wallpaper or try a different shell theme.Two screen shots with different themes.

---

### Post by linuxonbute on 2012-06-08
Thanks for the reply. Tried all the themes ( not tried installing extra ones ) and six different wallpapers with a range of colours/features and nothing made any difference I am afraid. 
The only thing which is clear is the current date. Everything else, month, other days and < and > navigation are seriously greyed out so they can hardly be seen.
I just wonder if there is some config file for the calendar itself with suitable options. I have tried looking for what might be one but not found it so far.
/etc/calendar/default points to /usr/share/calendar/calendar.all but it has nothing relating to what I would like in it.

---

### Post by Frogs Hair on 2012-06-08
Any adjustments would have to be made in the Gnome Shell theme CSS in usr/share/themes or .themes in home/hidden folders. I don't know my way around GTK 3 theme files.

Additional themes for Gnome 3.4  
[http://www.webupd8.org/2012/06/5-nice-gnome-34-themes-ubuntu-ppa.html](http://www.webupd8.org/2012/06/5-nice-gnome-34-themes-ubuntu-ppa.html)
[http://browse.deviantart.com/?qh=&section=&q=Gnome+3.4+themes](http://browse.deviantart.com/?qh=&section=&q=Gnome+3.4+themes)

---

### Post by Frogs Hair on 2012-06-08
It may be a Gnome problem so try restarting the shell . Alt + F2 ```
r
```

---

### Post by linuxonbute on 2012-06-09
> **Frogs Hair said:**
> Any adjustments would have to be made in the Gnome Shell theme CSS in usr/share/themes or .themes in home/hidden folders. I don't know my way around GTK 3 theme files.

Additional themes for Gnome 3.4  
[http://www.webupd8.org/2012/06/5-nice-gnome-34-themes-ubuntu-ppa.html](http://www.webupd8.org/2012/06/5-nice-gnome-34-themes-ubuntu-ppa.html)
[http://browse.deviantart.com/?qh=&section=&q=Gnome+3.4+themes](http://browse.deviantart.com/?qh=&section=&q=Gnome+3.4+themes)

Restarting gnome made no difference.
I had a look at the css files and some were over 2000 lines.
Many references to, for example @bg_color such as:
```


.button.default:active:hover:backdrop {
    background-image: -gtk-gradient (linear, left top, left bottom,
                                     from (mix (shade (@backdrop_selected_bg_color, 1.0), @bg_color, 0.3)),
                                     to (mix (shade (@backdrop_selected_bg_color, 1.1), @bg_color, 0.3)));

```
but could not find any definition for bg_color itself.
I guess I just do not understand what @bg_color means so unless I can find out more about it I will live with what I have or set up a different calendar.
Thanks again for your suggestions.

---

