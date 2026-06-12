---
title: "Xfce+conky?"
date: 2008-03-14
forum: Desktop Environments
---

### Post by Yes on 2008-03-14
When I run Conky in Xfce, it disappears after open a page above it (like Firefox).  Is there anything I can do about that, or does Conky not work in Xfce?

Here's my .conkyrc, if it matters:

```
own_window yes
own_window_hints undecorated,below,skip_taskbar
own_window_transparent yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color black
default_shade_color black
default_outline_color black

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

override_utf8_locale no
xftfont Purisa:size=13
xftalpha 0.8

TEXT
core0 ${cpu cpu0}% core1 ${cpu cpu1}% mem $mem root ${fs_used_perc /}% home ${fs_used_perc /home}% mail ${execi 300 gmail}
```

It also flickers sometimes when it updates, which didn't happen in Gnome.

---

