---
title: "Keep conky from disappearing when using show desktop?"
date: 2007-02-04
forum: Desktop Environments
---

### Post by oofnik on 2007-02-04
Hello,
I upgraded to Edgy not long ago and so far I'm really happy with it. I am using conky to display system stats, and every time I hit the show desktop button conky gets minimized too. The problem is, I can't bring it back up because I have it set not to show on the taskbar. So I have to kill the process and restart it, which is very annoying. Does anyone have an idea what I could do so the show desktop minimizes everything but conky (while still disabling its own taskbar icon)? Thanks!

My .conkyrc is attached, if that will help.

---

### Post by AndrewB on 2007-02-10
Here's my configuration file sans the TEXT portion. You can compare it to your's or copy and paste it in over your corresponding section of the config file.

```
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
own_window_hints below

# Xft font when Xft is enabled
xftfont Sans:style=Bold:size=10

# Text alpha when using Xft
xftalpha 1

# Print everything to stdout?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 1qq

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour hotpink

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 10

# border width
border_width 10

# Default colors and also border colors
#default_color white
#default_shade_color black
#default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 40
gap_y 40

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no


# Add spaces to keep things from moving about? This only affects certain objects.
use_spacer yes

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16)
min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
min_port_monitor_connections 256

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

```

Andrew

---

