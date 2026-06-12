---
title: "[SOLVED] Weird issues with Conky..."
date: 2008-03-19
forum: Desktop Effects &amp; Customization
---

### Post by j0nb0y22 on 2008-03-19
I set up conky the way I wanted... or so I thought.  Everytime I reboot conky is sitting over all my other windows and I cannot get to anything underneath it.  If I "killall conky" and run it again, it looks just fine.  I have it set up in Sessions to start when I log in just as "conky".  Am I doing something wrong?

Here is a pic to show you what it does each time I reboot before the "killall".

[IMG]http://i32.tinypic.com/xghzq9.png[/IMG]

> # UBUNTU-CONKY

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

update_interval 5.0

 

# Minimum size of text area

# minimum_size 250 5

 

# Draw shades?

draw_shades no

 

# Text stuff

draw_outline no # amplifies text

draw_borders no

font UnDotum:size=8

uppercase no # set to yes if you want all text to be in uppercase

 

# Stippled borders?

stippled_borders 3

 

# border margins

border_margin 9

 

# border width

border_width 10

 

# Default colors and also border colors, grey90 == #e5e5e5

default_color grey

 

own_window_colour black

own_window_transparent yes

 

# Text alignment, other possible values are commented

#alignment top_left

alignment top_right

#alignment bottom_left

#alignment bottom_right

 

# Gap between borders of screen and text

gap_x 10

gap_y 20

 

# stuff after 'TEXT' will be formatted on screen

 

TEXT

$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
 
${color orange}MEMORY / DISK ${hr 2}$color

ram:   $memperc%   ${membar 6}$color
swap:  $swapperc%   ${swapbar 6}$color
root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color
sd:    ${fs_free_perc /media/disk}%   ${fs_bar /media/disk}$color

${color orange}NETWORK (${addr ath0}) ${hr 2}$color
Down: $color${downspeed ath0} k/s ${alignr}Up: ${upspeed ath0} k/s
${downspeedgraph ath0 25,140 000000 ff0000} ${alignr}${upspeedgraph ath0
25,140 000000 00ff00}$color
Total: ${totaldown ath0} ${alignr}Total: ${totalup ath0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

---

### Post by aashay on 2008-03-19
Try this:
Make a file startconky.sh anywhere you like
put```
sleep 10 && conky
```in it. Make it executable ```
sudo chmod +x startconky.sh
```Run this file on startup instead of conky

---

### Post by j0nb0y22 on 2008-03-19
Awesome!!  Thanks! :KS

---

