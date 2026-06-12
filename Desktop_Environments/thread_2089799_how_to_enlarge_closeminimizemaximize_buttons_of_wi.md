---
title: "how to enlarge close/minimize/maximize buttons of window?"
date: 2012-11-30
forum: Desktop Environments
---

### Post by DrTebi on 2012-11-30
Hello,

I recently started using a high-resolution screen, and consequently all text, buttons, menus etc. are very tiny now. I have managed to enlarge most things, including the scrollbar width through a .gtkrc-2.0 file in my home directory.

What I just cannot figure out is how to get the close/minimize/maximize buttons of windows larger? I searched the GTK documentation, looked at theme how-tos but I just don't find anything :(

my gtkrc file now looks like this:

```
style "scroll"
{
    GtkScrollbar::slider-width = 25
    GtkToolbar::icon-size = 48
}

class "*" style "scroll"

```

This works fine for the slider width, but the icons of the window do not enlarge.

I am using the Ambiance theme that ships with Ubuntu 11.04, which I am running.

Thanks in advance for any help,,
DrTebi

---

### Post by shaktiman1234 on 2012-11-30
You might want to try different themes available on the internet. I also tried tweaking but could find the source. But using different theme did job for me.

---

### Post by DrTebi on 2012-11-30
Thanks for your reply.

I looked at a few different themes, but did not like them too much... I got so used to the Ambiance theme. Old men don't like change :)

There must be some kind of way to hack this... I feel comfortable going through code and configuration files; if I only knew where to find the setting/variable, it shouldn't be a problem.

---

### Post by DrTebi on 2012-12-01
OK, I sort of figured it out.

Those buttons are called "action" buttons and are defined in the metacity xml file of the theme (in my case "Ambiance").

Unfortunately, their sizes cannot be changed dynamically. Within the metacity directory of the theme directory are a bunch of PNG images that are used for this purpose. I resized these, and further I had to change the following width and heights in the metacity-theme-1.xml file:

```

<frame_geometry name="frame_geometry_normal" title_scale="medium" rounded_top_left="true" rounded_top_right="true"  rounded_bottom_left="true" rounded_bottom_right="true">
        [...]
	<distance name="button_width" value="40"/>
	<distance name="button_height" value="40"/>
        [...]
</frame_geometry>

<frame_geometry name="frame_geometry_abnormal" title_scale="medium" rounded_top_left="false" rounded_top_right="false">
        [...]
  	<distance name="button_width" value="40"/>
 	<distance name="button_height" value="40"/>
        [...]
</frame_geometry>

<frame_geometry name="geometry_maximized" rounded_top_left="false" rounded_top_right="false" rounded_bottom_left="false" rounded_bottom_right="false">
        [...]
  	<distance name="button_width" value="40"/>
  	<distance name="button_height" value="40"/>
        [...]
</frame_geometry>
```

This seems a bit complicated, considering how easy it is to change sizes of other things. Anyway, satisfied for now...

---

