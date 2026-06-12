---
title: "COnky font size not working"
date: 2007-11-16
forum: Desktop Effects &amp; Customization
---

### Post by fedex1993 on 2007-11-16
okay i am running 1.4.7 conky on my laptop and i am trying to change the size of my font for the clock and also change the type of font. Here is my conky config 
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
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
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
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${time %I:%M %P}

```
is there anyway that i can change the font and font type and size to bigger from my conky script?

---

### Post by fedex1993 on 2007-11-16
okay am i in the wrong place or does no one feal like helping wow

---

### Post by themtx on 2007-11-16
Try changing "use_xft yes", then adding "xftfont arial:size=8" (or whatever you like), and commenting out "font arial"

Allows use of anti-aliased fonts, which IMO look better.

---

### Post by fedex1993 on 2007-11-16
thank themtx i love you man but not in a gay way thanks some achley helps i give a thumbs up):P

---

### Post by themtx on 2007-11-16
NP at all, man.

Just for grins I added my own .conkyrc.  You'll need to adjust the filesytem monitor, and remove hd temp if you don't have hddtemp running...

---

### Post by minutero on 2008-04-07
try using ${font Zekton:style=Bold: pixelsize=42} TEXT $font that work for me

---

