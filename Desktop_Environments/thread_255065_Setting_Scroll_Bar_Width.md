---
title: "Setting Scroll Bar Width"
date: 2006-09-10
forum: Desktop Environments
---

### Post by jredelfs on 2006-09-10
How do I set the width of the scroll bar on the right hand side of most windows?  If this information is included in the documentation, I have been unable to find it.

---

### Post by chavo on 2006-09-11
You can't set it with a GUI but it's easy to tweak the GTK theme.
First run this command
```

gedit ~/.gtkrc-2.0

```

Now paste this in and then save it.
```

style "scroll"
{
    GtkScrollbar::slider-width        = 25
}

class "*" style "scroll"

```

Make sure you change the 25 to whatever width you like. 25 is pretty wide, I'm just using it as an example.
You can use the .gtkrc-2.0 file to control a lot of GTK widgets. Or you can edit the theme directly. I usually make a copy of the system theme and put it in ~/.themes before I edit those.

---

### Post by kona0197 on 2007-12-22
When I type "gedit ~/.gtkrc-2.0" in my terminal it brings up a blank page. Is that what I want?

---

### Post by quadra on 2008-01-13
Yes, seems the file is not existing by default. Worked fine for me.

---

