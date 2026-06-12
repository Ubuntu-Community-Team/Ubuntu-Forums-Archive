---
title: "Conky disappears after I click anywhere else on desktop"
date: 2010-01-01
forum: Desktop Environments
---

### Post by phillychease on 2010-01-01
or when i open a window and click on the desktop.
and how do i make conky run on start up? thanks!

---

### Post by McDarling on 2010-01-01
Okay, I'm in Xubuntu, so this could be a little different for you, but here's what I did. I created a script called .conky or something, and put it in my home directory. Then I went into Applications, then Settings, then Session and Startup, and it's pretty clear what to do from there with adding the .conky script to one of the default startup applications. I don't know why it keeps going below your desktop, but that's how you set it up to start automatically.

---

### Post by phillychease on 2010-01-01
yea i made a script

```
#!/bin/bash
sleep 20 &&
conky &
exit
```

and ran it on startup.
it runs but after i open a windows, say firefox, and i click my desktop it disappears.

---

### Post by phillychease on 2010-01-02
ok i got it when i run it, it doesnt disappear, but now when i open a window and click on the desktop conky disappears but it's still running...
heres my config
```
#Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type desktop override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 200

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color grey
own_window_colour grey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 35

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

```

---

### Post by phillychease on 2010-01-02
nvm i got it
set
set own_window_type to normal or override, not desktop

---

