---
title: "Conky stay on desktop problem"
date: 2007-12-14
forum: Desktop Effects &amp; Customization
---

### Post by 98GreenGT on 2007-12-14
Conky is set to start up with my computer by default.  But when I open something the conky app with part of my desktop background is always set above everything.  Any ideas as to why this is happening?

---

### Post by pebo on 2007-12-14
In your .conkyrc the following works for me:```
# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type desktop

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour hotpink

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

---

