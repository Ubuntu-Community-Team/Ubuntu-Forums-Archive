---
title: "Why is conky doing this?"
date: 2009-06-08
forum: Desktop Environments
---

### Post by illogic6 on 2009-06-08
[http://img32.imageshack.us/img32/5702/screenshotjas.png](http://img32.imageshack.us/img32/5702/screenshotjas.png)

I'm pretty sure I've gotten it to be completely transparent before.  Now I have this barely visible, yet annoying border running around it.

I've looked around for an answer, but I haven't been able to narrow it down.  I'm sorry if this is the 100th time this question has been posted.

Here's my conkyrc:

```

# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background no

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

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour hotpink

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

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

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
#stippled_borders 8

# border margins
border_margin 4

# border width
border_width 0

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 0
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
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

# Shows the maximum value in scaled graphs.
show_graph_scale no

# Shows the time range covered by a graph.
show_graph_range no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# Timing interval for music player thread, e.g. mpd, audacious
#music_player_interval (update_interval is default)

# Strictness of if_up. One of: up, link or address. The later ones imply the further ones.
# Defaults to up.
#if_up_strictness address

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
default_color FFFFFF
# stuff after 'TEXT' will be formatted on screen
background black
TEXT
         ${font Hand Of Sean:size=14}${time %A %d %Y}
            ${font Hand Of Sean:size=55}${time %H:%M}

```

---

### Post by mtbsoft on 2009-06-09
Took me long enough to work out what you were actually displaying via conky!

It's not conky, it looks like you've enabled drop-shadow on your windows in the window manager, there are a number of options in compiz (if that's what you're using) which can result in this sort of window decoration (e.g. reflection).

Since you are rendering conky in its own window, it gets decorated just the same as any other window, despite having no borders - open any app. and you'll see the same drop-shadow on the window.

---

### Post by n0_mad on 2009-06-09
try to set
own_window_type override

---

### Post by VCoolio on 2009-06-09
If you use compiz you can disable dropshadows for conky in the window decoration plugin. In the entry for shadow windows fill in "any !conky" or "any & !(class=Conky)" (without the ""), play with it to see what works.

---

### Post by illogic6 on 2009-06-10
You guys are awesome.  I would have never found that on my own.

Thanks! :mrgreen:

---

