---
title: "lm-sensors and conky not working"
date: 2007-12-21
forum: Desktop Effects &amp; Customization
---

### Post by Scarlett on 2007-12-21
I've got lm-sensors installed but I'm not sure it's working correctly.  I just had some work done on my box, part of which was supposed to improve the air-flow, but even so, the temperature read-outs from lm-sensors seems low.  The core temp is at 29C when it used to idle at about 45C (according to Windows.)  I've got one temp, and I can't tell which device it's reading - it only says temp2, is at -20C.  Yeah, negative 20 celcius!  I'm pretty sure that even my freezer isn't that cold.

In Conky, the only temperature I have it set to read is the two CUPs but they just show 0.  I checked my hardware and somewhere in the description I saw acpi, which is what Conky is supposed to be reading.  But it doesn't.  

This is my Conkyrc file 

```
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
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
#minimum_size 299 5
minimum_width 299
maximum_width 300

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
xftfont DejaVu Sans Condensed Bold:size=10
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 100

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color white}SYSTEM ${hr 2}$color
AMD Athlon 64 X2 Dual Core $color
$nodename $sysname $kernel on $machine


${color white}CPU ${hr 2}$color
${offset 10}${color lightgrey}CPU1 Usage:${color} ${cpu cpu1}% ${freq cpu1}MHz   Temp: ${acpitemp}${cpubar cpu1}
${offset 10}${color lightgrey}CPU2 Usage:${color} ${cpu cpu2}% ${freq cpu2}MHz   Temp: ${acpitemp}${cpubar cpu2}
${cpugraph 000000 0236FD}
${color lightgrey}Highest CPU:
${offset 10}${color lightgrey} ${top name 1} ${alignr}${offset -125}${top cpu 1}
${offset 10}${color lightgrey} ${top name 2} ${alignr}${offset -125}${top cpu 2}
${offset 10}${color lightgrey} ${top name 3} ${alignr}${offset -125}${top cpu 3}

```  

So, is lm-sensors working correctly?
I've got a core temp (I'm assuming that's the general temp inside the box), 2 temp 1's (the dual core CPU?) and what is temp3?
How do I make Conky display the correct temps?

---

