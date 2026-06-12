---
title: "[SOLVED] How to move conky"
date: 2008-01-20
forum: Desktop Effects &amp; Customization
---

### Post by Fraser from Scotland on 2008-01-20
Hi, I have conky setup, but it overlaps the top panel and I'm not sure how to move it down as I didn't make the .conkyrc file. Here is a screenshot and my .conkyrc

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

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
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}

${offset 240}${color slate grey}FILESYSTEM:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}



Sorry I don't know how to put it in a code box :(

[http://img256.imageshack.us/img256/8937/screenshotzh0.png](http://img256.imageshack.us/img256/8937/screenshotzh0.png)

---

### Post by mik01aj on 2008-01-20
```
# Gap between borders of screen and text
gap_x 10
gap_y 10
```Just modify these lines ;)

---

### Post by Fraser from Scotland on 2008-01-20
Thank you :) for some reason conky closed and fixed itself, but i know nothing can ever "fix" itself so now I know what to do if it happens again.

---

