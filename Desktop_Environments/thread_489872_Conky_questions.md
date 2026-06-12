---
title: "Conky questions"
date: 2007-07-01
forum: Desktop Environments
---

### Post by jba6511 on 2007-07-01
I want to:
1) change the text to a much smaller size as I am using a thinkpad t60 laptop for conky
2) have conky start up when ubuntu starts. I tried adding conky to sessions just using the command conky. I have compiz manager if that matters.
Here is a copy of .conkyrc:

[PHP]# UBUNTU-CONKY
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
own_window no
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
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
xftfont You Rook Marbelous:size=12
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color E5DBC6

own_window_colour black
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
${color cd4d00}SYSTEM ${hr 5}$color
$nodename $sysname $kernel on $machine
$uptime

${color cd4d00}${pre_exec cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${hr 5}$color
${freq_dyn}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}

${color cd4d00}PROCESSES ${hr 5}$color
Process Number:  $processes       Running:  $running_processes

${color cd4d00}HIGHEST CPU ${stippled_hr 1}$color
NAME${alignr 9}PID      CPU%      MEM%
${top name 1}${alignr 9}${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2}${alignr 9}${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3}${alignr 9}${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4}${alignr 9}${top pid 4}   ${top cpu 4}    ${top mem 4}

${color cd4d00}HIGHEST MEM ${stippled_hr 1}$color
NAME${alignr 9}PID      CPU%      MEM%
${top_mem name 1}${alignr 9}${top_mem pid 1}   ${top_mem cpu 1}    ${top_mem mem 1}
${top_mem name 2}${alignr 9}${top_mem pid 2}   ${top_mem cpu 2}    ${top_mem mem 2}
${top_mem name 3}${alignr 9}${top_mem pid 3}   ${top_mem cpu 3}    ${top_mem mem 3}
${top_mem name 4}${alignr 9}${top_mem pid 4}   ${top_mem cpu 4}    ${top_mem mem 4}

${color cd4d00}RAM ${hr 5}$color
$mem / $memmax
$memperc%   ${membar 6}$color

${color cd4d00}SWAP ${hr 5}$color
$swap / $swapmax
$swapperc%   ${swapbar 6}$color

${color cd4d00}HARDDRIVE ${hr 5}$color
Total:	${fs_used /} / ${fs_size /} 
${fs_free_perc /}%   ${fs_bar 6 /}$color 

${color cd4d00}NETWORK (${addr eth0}) ${hr 5}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 00ff00} ${alignr}${upspeedgraph eth0 25,140 000000 ff0000}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} ${alignr}Outbound: ${tcp_portmon 32768 61000 count}
Total: ${tcp_portmon 1 65535 count}[/PHP]

---

### Post by Nythain on 2007-07-01
you can set the default font like this
```

# Xft font when Xft is enabled
xftfont DejaVu Sans Mono:size=12

```
anywhere in the top section, making sure to change the font you want to use, and the appropriate size... at least thats how i did it... im sure there's an easier way...
to change the size throughout the bottom part (everything after TEXT
```

${font :size=18}${time %A %B %d}${alignr}${time %I:%M %P}$font

```
is an example... basically change the size with ${font:size=##} then make sure you end the line with $font to go back to your default font

---

### Post by kerry_s on 2007-07-01
change this line->
xftfont You Rook Marbelous:size=12 
to
xftfont You Rook Marbelous:size=8

---

