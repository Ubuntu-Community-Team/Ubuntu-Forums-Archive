---
title: "conky is hogging resources"
date: 2009-01-09
forum: General Help
---

### Post by nlz on 2009-01-09
Conky is using 10 - 15% of my resources, which is a bit crazy since I have a Intel P4 3 GHZ dual core processor. Here is my .conkyrc

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
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
"xftfont arial:size=16"

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

maximum_width 280
minimum_size 280

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
gap_x 30
gap_y 30

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}

${color #ffcb48}Processes ${hr 2}
${color #98c2c7}NAME                PID      CPU%      MEM%
${color #e5e5e5}${top name 1}	${top pid 1}	${top cpu 1}	${top mem 1}
${color #e5e5e5}${top name 2}	${top pid 2}	${top cpu 2}	${top mem 2}
${color #e5e5e5}${top name 3}	${top pid 3}	${top cpu 3}	${top mem 3}
${color #e5e5e5}${top name 4}	${top pid 4}	${top cpu 4}	-get ${top mem 4}

${color orange}Highest MEM: ${hr 2}$color
  ${color #98c2c7}NAME               MEM%   PID 
  ${color lightgrey} ${top_mem name 1}${top_mem mem 1}${top_mem pid 1}
  ${color lightgrey} ${top_mem name 2}${top_mem mem 2}${top_mem pid 2}
  ${color lightgrey} ${top_mem name 3}${top_mem mem 3}${top_mem pid 3}
  ${color lightgrey} ${top_mem name 4}${top_mem mem 4}${top_mem pid 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color
Home:  ${fs_free_perc /home}%   ${fs_bar 6 /home}$color

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

Uptime: $uptime

```

---

### Post by Harii on 2009-01-10
try only using one color,change Update interval lower and set 
--use_xft no


see if that lowers it?
keep it simple --it help on mine.

---

