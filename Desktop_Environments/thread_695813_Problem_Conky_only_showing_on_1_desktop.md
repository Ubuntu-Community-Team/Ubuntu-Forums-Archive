---
title: "Problem: Conky only showing on 1 desktop"
date: 2008-02-13
forum: Desktop Environments
---

### Post by bdtgp on 2008-02-13
How do I get conky to show on all 4 workspaces?  Currently it only shows on my first desktop.   Here is my .conkyrc file:
```
# conky configuration
# edited by brett

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
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Terminus:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Messes with the conky window
own_window yes
own_window_hints undecorated,below,skip_taskbar
own_window_type normal
own_window_transparent yes
background no

# Use double buffering to reduce flicker
double_buffer yes

# Minimum size of text area
minimum_size 150 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

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
use_spacer yes
#Note: doesn't work in conky 1.2 =(



# stuff after 'TEXT' will be formatted on screen

TEXT



${color slate grey}${time %a, } ${color }${time %e %B %G}
${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${color slate grey}UpTime: ${color }$uptime
${color slate grey}Kern:${color }$kernel
${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${cpugraph cpu0 30,150 000000 ffffff}
${cpugraph cpu1 30,150 000000 ffffff}
${color slate grey}Load: ${color }$loadavg
${color slate grey}Processes: ${color }$processes  
${color slate grey}Running:   ${color }$running_processes

${color slate grey}Highest CPU:
${color #ddaa00} ${top name 1}${top_mem cpu 1}
${color lightgrey} ${top name 2}${top cpu 2}
${color lightgrey} ${top name 3}${top cpu 3}
${color lightgrey} ${top name 4}${top cpu 4}

${color slate grey}Highest MEM:
${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${membar 3,100}
${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${swapbar 3,100}

${color slate grey}ROOT:    ${color }${fs_used /}/${fs_size /}
${fs_bar 6,100 /}
${color slate grey}HOME:  ${color }${fs_used /home}/${fs_size /home}
${fs_bar 6,100 /home}
${color slate grey}NET: 
${color}Up: ${color }${upspeed eth0} k/s
${upspeedgraph eth0 30,150 000000 ffffff}
${color}Down: ${color }${downspeed eth0}k/s${color}
${downspeedgraph eth0 30,150 000000 ffffff}
```

Thanks.

---

### Post by xoai on 2008-02-13
own_window yes
own_window_hints undecorated,below,[COLOR="Red"]sticky,[/COLOR]skip_taskbar
own_window_type normal
own_window_transparent yes
background no

Just add more **"sticky"**, conky will be displayed on all workspaces.

---

### Post by bdtgp on 2008-02-14
That worked.  Thanks.

---

