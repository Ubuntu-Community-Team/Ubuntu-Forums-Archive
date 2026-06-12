---
title: "Openbox and Missing Conky"
date: 2009-12-31
forum: Desktop Environments
---

### Post by Nyken on 2009-12-31
Hello,

I switched my window manager from xwfm4 to openbox with my Xubuntu installation, Problem now is that Conky is missing, even though it's still as startup item. 

Basically, anyone else have this problem, and, if so, how did you get it to automatically come up again?

---

### Post by Nyken on 2009-12-31
Marking this one solved. Found out it was a problem with my .conkyrc. I played with it and changed it line by line and experiements a little.

First, Here is how I have it set up:

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
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_class Conky

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#font arial
xftfont arial:size=9
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 30

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

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

# stuff after ‘TEXT’ will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz Load: ${loadavg} Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME PID CPU% MEM%
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM: $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

sda1: ${fs_free_perc /}% ${fs_bar 6 /}$color
sdb1: ${fs_free_perc /media/sdb1}% ${fs_bar 6 /media/sdb1}$color
sdb5: ${fs_free_perc /media/sdb5}% ${fs_bar 6 /media/sdb5}
sdb6: ${fs_free_perc /media/sdb6}% ${fs_bar 6 /media/sdb6}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

What made it work, was I had to change the variable "own_window_type" from override to normal. Override will make it not work.

Hope someone else comes up on this, if they ever find they need help. By the way, this thread showed up on Google 5 minutes after I began it. Amazing!

---

