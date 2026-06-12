---
title: "Share your Software and Utilities"
date: 2010-09-03
forum: Desktop Environments
---

### Post by dontgetshocked on 2010-09-03
Feel like sharing some of your favorite software goodies?
Maybe you have some tweaks that you would like to share!
Themes,Sounds,Tweaks,Utilities,etc...):P

---

### Post by nick_goodfate on 2010-09-03
I have removed all gnome panels and replaced them with AWN. In my opinion AWN is the best panel replacement(for example you can have notification area with it) and it can be really beautiful too! My favorite applet of this dock is [[COLOR="Purple"]RELATED[/COLOR]]("http://www.khattam.info/howto-install-zeitgeist-related-applet-for-avant-window-navigator-2010-08-14.html") applet.

Deleting all gnome panels you loose Alt+F2 launcher. Gnome-do from repositories replaced it for me.

I also have a really simple conky displaying date and time. My .conkyrc file:
```
# Use Xft?
use_xft yes
xftfont Droid Sans:size=6
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 3

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
own_window_class conky
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 0 0
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
border_inner_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color LightCyan
default_shade_color black
default_outline_color black
own_window_colour black
color1 black

# Text alignment, other possible values are commented
#alignment middle_middle
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 20
gap_y 0

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

TEXT
${font :size=10}${offset 10}${color grey}${time %A}  ${time %B %e, %G} 
${font :size=50}${color grey}${time %H:%M} 
```

Finally i m using [[COLOR="Purple"]Elegant[/COLOR]]("http://art.ubuntuforums.org/showthread.php?p=9797325") theme and [[COLOR="Purple"]Faenza[/COLOR]]("http://tiheum.deviantart.com/art/Faenza-Icons-173323228") icons.

[[COLOR="Purple"]My desktop[/COLOR]]("http://tinypic.com/r/2mcakc4/7") :D

---

