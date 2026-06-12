---
title: "Gnome Color Chooser in Ubuntu 16.04"
date: 2016-10-16
forum: Desktop Environments
---

### Post by RogerDavis on 2016-10-16
Gnome Color Chooser doesn't seem to work.  I want to increase the width of the scroll bars under the "Specific" tab.  I can set it wherever I want, click Apply, but no change happens.

This is all I really want to change right now, but I did try other things with no result.

Do I need to unprotect some file, or some other non-obvious thing?

---

### Post by vasa1 on 2016-10-16
IIRC, it's only for gtk2 apps.

---

### Post by CantankRus on 2016-10-16
What theme are you using?

---

### Post by RogerDavis on 2016-10-17
I'm using Radiance, with many tweaks.

I'm missing only two things, the width of the scroll bars on all apps, etc., and to change the "pumpkin" and it's other round friends to square window control buttons of another color.

Because of the difficulty of doing these things, I've considered adding more themes that might have the basic features I need, but it's very unclear how to add themes, and how to find simple basic themes.  It seems that for most, the wilder the better.  I want something like Windoze XP.

If Color Chooser doesn't work in GTK3, is there something else like it?

Thanks!

---

### Post by vasa1 on 2016-10-17
You have two issues: scrollbars and window buttons. Please try to have one issue per thread with an appropriately descriptive title. Otherwise, things can get confusing and you may not get the help you need.

---

### Post by CantankRus on 2016-10-17
You can place themes in ...
[LIST]
[*]**/usr/share/themes** ......requires root access
[*]**~/.themes **....can just be copied pasted after extracting the theme folder.
[/LIST]

You can also install themes directly from [**_[COLOR="#B22222"]gnome-look[/COLOR]_**]("https://www.gnome-look.org/browse/cat/135/ord/latest/")
On gnome-look, if you go to the files tab of a selected theme you can install just by clicking the install button.
An application called xdgurl must be installed first. Click the ? icon to see how.
xdgurl will install themes to ~/.themes.
[ATTACH=CONFIG]271661[/ATTACH]  

I'm no expert on this but have found a few things by just poking around.
You can create a file **~/.config/gtk-3.0/gtk.css** to override theme settings. If you don't have a  ~/.config/gtk-3.0 folder ...create it.
This is my ~/.config/gtk-3.0/gtk.css file which stops the scrollbar from narrowing to a few pixels and also sets the width with the first setting...**GtkRange-slider-width**.
```
 /*************
 * scrollbar *
 *************/
.scrollbar {    
    -GtkRange-slider-width: 12;
}



/* Adding margins, so actual visible size is: -GtkRange-slider-width - margin
 * this allows to define some kind of proximity effect also on mouse-enter
 */
.scrollbar.slider.vertical:dir(ltr):not(:hover):not(.dragging) {
    margin-left: 0px;
}

.scrollbar.slider.vertical:dir(rtl):not(:hover):not(.dragging) {
    margin-right: 0px;
}

.scrollbar.slider.horizontal:not(:hover):not(.dragging) {
    margin-top: 0px;
}



/* Adding margins, so actual visible size is: -GtkRange-slider-width - margin
 * this allows to keep the slider smaller, but keeping few threshold pixels
 */
.scrollbar.vertical:hover:dir(ltr),
.scrollbar.vertical.dragging:dir(ltr) {
    margin-left: 0px;
}

.scrollbar.vertical:hover:dir(rtl),
.scrollbar.vertical.dragging:dir(rtl) {
    margin-right: 0px;
}

.scrollbar.horizontal:hover,
.scrollbar.horizontal.dragging,
.scrollbar.horizontal.slider:hover,
.scrollbar.horizontal.slider.dragging {
    margin-top: 0px;
}


/* slider color and radius */
.scrollbar.slider {
    background-color: alpha(@selected_bg_color, 0.6);
    border-radius: 5px;
}

.scrollbar.slider.hovering,
.scrollbar.slider.dragging {
    background-color: alpha(@selected_bg_color, 0.8);
    border-radius: 5px;
}
```
When you make changes logout and back in.

_Normal Radiance_
[ATTACH=CONFIG]271662[/ATTACH]

_Radiance using ~/.config/gtk-3.0/gtk.css_
[ATTACH=CONFIG]271663[/ATTACH]

---

