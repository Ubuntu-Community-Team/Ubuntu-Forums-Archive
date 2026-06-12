---
title: "Gnome menu dotted border"
date: 2011-01-14
forum: Desktop Environments
---

### Post by morefeo on 2011-01-14
Hi, sometimes the gnome menu icon shows a dotted border when I click in any application of the same panel, like this:
[IMG]http://img254.imageshack.us/img254/9803/exam.png[/IMG]

It doesn't happen always, when I boot it's not shown, but after a while the dotted border appears. I edited my gtkrc-2.0 file for removing the arrow it had, don't know if it is the cause:
> style "panel-arrow-remove"

#the following removes the arrows from the panel
{
engine "pixmap"
    {
    image
    {
        function    = ARROW
        recolorable    = TRUE
        overlay_file    = "arrows/arrow-blank.png"
        overlay_border    = {2,2,2,2}
        overlay_stretch    = FALSE
        arrow_direction    = UP
    }

    image
    {
        function    = ARROW
        recolorable    = TRUE
        overlay_file    = "arrows/arrow-blank.png"
        overlay_border    = {2,2,2,2}
        overlay_stretch    = FALSE
        arrow_direction    = DOWN
    }
    }
}

widget_class "*PanelToplevel*"             style "panel-arrow-remove"

How I fix it?

---

### Post by cmoraes on 2011-01-14
is there an image supposed to be attached to your post?

---

### Post by morefeo on 2011-01-14
It's linked from imageshack...I'll attach it anyways.

---

