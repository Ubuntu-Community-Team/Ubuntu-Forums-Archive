---
title: "conky with xwinwrap"
date: 2009-01-24
forum: General Help
---

### Post by xoron on 2009-01-24
hi

i had conky working at first but it no longer works while i have xwinwrap on...i have seen videos on youtube showing it working but i cant work out how here is my conky configuration:

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
on_bottom yes
#own_window yes
#own_window_hints undecorated,below,skip_taskbar
#background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 0.5

# Minimum size of text area
minimum_size 160 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right


# Gap between borders of screen and text
gap_x 10
gap_y 50

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${color slate grey}${time %a, } ${color }${time %e %B %G}
${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${color slate grey}UpTime: ${color }$uptime
${color slate grey}Kern:${color }$kernel
${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${cpugraph 20,130 000000 ffffff}
${color slate grey}Load: ${color }$loadavg
${color slate grey}Processes: ${color }$processes  
${color slate grey}Running:   ${color }$running_processes

${color slate grey}Highest CPU:
${color #ddaa00} ${top name 1}${top_mem cpu 1}
${color lightgrey} ${top name 2}${top cpu 2}
${color lightgrey} ${top name 3}${top cpu 3}
${color lightgrey} ${top name 4}${top cpu 4}
${color lightgrey} ${top name 5}${top cpu 5}
${color lightgrey} ${top name 6}${top cpu 6}

${color slate grey}Highest MEM:
${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${color lightgrey} ${top_mem name 4}${top_mem mem 4}
${color lightgrey} ${top_mem name 5}${top_mem mem 5}
${color lightgrey} ${top_mem name 6}${top_mem mem 6}

${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${membar 3,100}
${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${swapbar 3,100}

${color slate grey}NET: 
${color}Up: ${color }${upspeed eth0} k/s
${upspeedgraph eth0 20,130 000000 ffffff}
${color}Down: ${color }${downspeed eth0}k/s${color}
${downspeedgraph eth0 20,130 000000 ffffff}

${color slate grey}LOGGING:
${color}${execi 30 tail -n3 /var/log/messages | fold -w50}

${color slate grey}SECURITY:
${color}${execi 30 tail -n3 /var/log/auth.log | fold -w50}


```


please ask if more information is needed

thanks in advanced

---

### Post by easybake on 2009-01-24
Run xwinwrap and then start conky through terminal. Post the print out on here.

---

### Post by xoron on 2009-01-25
i ran conky through terminal and it shows that  it is running...however it is running behind xwinwrap... i know because it is there when i close xwinwrap:

~$ killall xwinwrap

---

