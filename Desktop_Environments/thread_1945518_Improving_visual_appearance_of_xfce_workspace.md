---
title: "Improving visual appearance of xfce workspace"
date: 2012-03-23
forum: Desktop Environments
---

### Post by sirriffsalot on 2012-03-23
Hey all!

I have xfce-dusk set as my appearance package in the settings option, and I like it very much. Only problem that I have is that the colours of the workspace switcher are so dark that I have difficulty at times seeing which workspace I am currently in... Is there any way of editing the colours of this portion of the top panel so I can switch without having to zoom in on the screen with my eyes to see which one has the "dark blue" in it (that's the current workspace color being very invisible in contrast with the black background)...?:)

Cheers!

---

### Post by Toz on 2012-03-23
Try this in your ~/.gtkrc-2.0 file:
```

style "pager" = "default"
{
    bg[NORMAL]        = "#000000"	# background colour
    bg[PRELIGHT]      = "#ff0000"	# foreground colour on hover
    bg[SELECTED]      = "#0000ff"	# foreground colour
}
widget_class "*Pager*"             style "pager"
class "*Pager*"                    style "pager"

```
...adjust values to suit.

---

### Post by sirriffsalot on 2012-03-26
Hello again, Toz!

Thanks again for fantastic help! Are you writing these things as requests come in or are you getting it from somewhere? If the latter, would you mind pointing me to where so I won't have to bother you and others?:)

Thanks once again!

---

### Post by Toz on 2012-03-26
I rely mostly on past experiences. However, most of this information already exists in the different theme files that in /usr/share/themes. Reviewing those theme files (making a copy and playing with the settings) helps to understand how things work. Knowing what to look for seems to big thing though. I also refer occasionally to the gtk documentation to help identify what I'm looking for ([per.gnome.org/gtk/stable/]("per.gnome.org/gtk/stable/") and specifically about the different widgets: [http://developer.gnome.org/gtk/stable/gtkobjects.html]("http://developer.gnome.org/gtk/stable/gtkobjects.html")).

---

