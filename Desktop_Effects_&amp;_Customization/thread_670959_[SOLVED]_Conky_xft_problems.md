---
title: "[SOLVED] Conky xft problems"
date: 2008-01-18
forum: Desktop Effects &amp; Customization
---

### Post by FuturePilot on 2008-01-18
I'm having a bit of an issue with the xft option. If I enable use_xft it throws the alignment of my process off. But if I disable use_xft they are perfectly lined up. The screenshot might explain it a bit better. The top one is without xft, the bottom one is with xft. Is there anyway to keep them aligned while using xft?
Here's my conkyrc
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
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline yes # amplifies text if yes
draw_borders no
xftfont sans:size=8
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color ffffff 

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 2
gap_y 14

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color light blue}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
Uptime: $uptime

${color light blue}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitempf}
$cpubar
${cpugraph ADD8E6 ffffff}
${color light blue}NAME$color                ${color light blue}PID$color      ${color light blue}CPU%$color      ${color light blue}MEM%$color
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color light blue}MEMORY USED ${hr 2}$color
RAM: $mem / $memmax
$memperc% ${membar 6}$color

Swap: $swap / $swapmax 
$swapperc% ${swapbar 6}$color

${color light blue}DISK USED ${hr 2}$color
Root:   ${fs_used_perc /}% ${color #ffffff}${fs_bar 6 /}$color 

I/O: ${color #ffffff}$diskiograph$color

${color light blue}NETWORK (${addr eth0}) ${hr 1}$color
${color light blue}Down: ${color white}${downspeed eth0}k/s ${alignr}${color light blue}Up: ${color white}${upspeed eth0}k/s
${downspeedgraph eth0 25,140 ffffff ADD8E6} ${alignr}${upspeedgraph eth0 
25,140 ffffff ADD8E6}
${color light blue}Total: ${color white}${totaldown eth0} ${alignr}${color light blue}Total: ${color white}${totalup eth0}
${color light blue}Inbound: ${color white}${tcp_portmon 1 32767 count} ${color light blue}Outbound: ${color white}${tcp_portmon 32768 
61000 count}${alignr}${color light blue}Total: ${color white}${tcp_portmon 1 65535 count}
${color light blue}Connections ${color white}${tcp_portmon 32768 61000 count}

${color light blue}LOGGING ${hr 2}$color
${execi 30 tail -n4 /var/log/messages | fold -w50}
```

---

### Post by FuturePilot on 2008-01-19
:-\"

---

### Post by FuturePilot on 2008-01-23
Anyone? :sad:

---

### Post by jmikola on 2008-02-23
I'm using Conky for column output as well (using top, vs. tcp_portmon in your case), and I'm pretty sure your problem is with using a variable-width font, rather than Xft.  Try replacing Sans with a monospace font (e.g. Bitstream Vera Sans Mono).

---

### Post by kerry_s on 2008-02-23
yep, if you want that section to hold still add a font entry for mono:size=8.
```
${font mono:size=8}
```

see pic
updated: see pic 2, just change it for the section that moves, use sans for the rest, it looks better.

---

### Post by FuturePilot on 2008-02-24
> **jmikola said:**
> I'm using Conky for column output as well (using top, vs. tcp_portmon in your case), and I'm pretty sure your problem is with using a variable-width font, rather than Xft.  Try replacing Sans with a monospace font (e.g. Bitstream Vera Sans Mono).

> **kerry_s said:**
> yep, if you want that section to hold still add a font entry for mono:size=8.
```
${font mono:size=8}
```

see pic
updated: see pic 2, just change it for the section that moves, use sans for the rest, it looks better.

Thank you both! :D With your help they are now all lined up nicely :guitar:

---

### Post by kerry_s on 2008-02-24
you know before you mentioned it, i never really looked at it. :)
now i got mine all lined up as well and it does look much better.
pic

---

### Post by moore.bryan on 2008-04-17
> **kerry_s said:**
> yep, if you want that section to hold still add a font entry for mono:size=8.
```
${font mono:size=8}
```see pic
updated: see pic 2, just change it for the section that moves, use sans for the rest, it looks better.
this doesn't fix anything for me; any ideas?

---

