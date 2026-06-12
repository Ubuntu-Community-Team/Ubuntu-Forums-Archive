---
title: "Conky can't make it all the way to upper left corner"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by orb9220 on 2007-04-25
Well it was working all the way in upper left corner flushed. But had to change it to own window yes to get desktop icons back.

config:

> background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Terminus:size=8

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
#own_window no
#own_window yes
#own_window_type override
#own_window_transparent 1

own_window yes
own_window_transparent yes
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 300 5

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
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x -0
gap_y -0

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

TEXT

${offset 10}${color }${time %a, } ${color }${time %e %B %G}
${offset 10}${color }${time %Z,    }${color }${time %I:%M:%S %A}
${offset 10}${color }UpTime: ${color }$uptime
${offset 10}${color }Kern:${color }$kernel
${offset 10}${color #ddaa00}CPU:${color } $cpu%
${offset 10}${cpugraph 20,130 000000 ffffff}
${offset 10}${color #ddaa00}Load: ${color }$loadavg
${offset 10}${color #ddaa00}Processes: ${color }$processes  
${offset 10}${color #ddaa00}Running:   ${color }$running_processes

${offset 10}${color slate grey}Highest CPU:
${offset 10}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 10}${color lightgrey} ${top name 2}${top cpu 2}
${offset 10}${color lightgrey} ${top name 3}${top cpu 3}
${offset 10}${color lightgrey} ${top name 4}${top cpu 4}

${offset 10}${color slate grey}Highest MEM:
${offset 10}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 10}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 10}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 10}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 10}${color #ddaa00}MEM:  ${color } $memperc% $mem/$memmax
${offset 10}${membar 3,100}
${offset 10}${color #ddaa00}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 10}${swapbar 3,100}

${offset 10}${color #ddaa00}ROOT:    ${color }${fs_free /}
${offset 10}${fs_bar 3,100 /}
${offset 10}${color #ddaa00}HOME:  ${color }${fs_free /home}
${offset 10}${fs_bar 3,100 /home}
${offset 10}${color #ddaa00}Data-fat32:  ${color }${fs_free /home/orb/Drives/114GB-fat32}
${offset 10}${fs_bar 3,100 /home/orb/Drives/114GB-fat32}
${offset 10}${color #ddaa00}NET: 
${offset 10}${color}Up: ${color }${upspeedf ath0} kB/s
${offset 10}${upspeedgraph ath0 20,130 000000 ffffff}
${offset 10}${color}Down: ${color }${downspeedf ath0}kB/s${color}
${offset 10}${downspeedgraph ath0 20,130 000000 ffffff}
${offset 10}${color}Link Status: ${color }${linkstatus ath0}
${offset 10}${color}IP: ${addr ath0}

Just want to get it flushed to top left corner see pic.

EDIT:  NEVERMIND!  just figured it out by see all the extra lines between

TEXT

.                                 [B] <----- All this space the offender
[/B]
${offset 10}${color }${time %a, } ${color }${time %e %B %G}
${offset 10}${color }${time %Z,    }${color }${time %I:%M:%S %A}
${offset 10}${color }UpTime: ${color }$uptime
${offset 10}${color }Kern:${color }$kernel
${offset 10}${color #ddaa00}CPU:${color } $cpu%
${offset 10}${cpugraph 20,130 000000 ffffff}...etc

---

### Post by notwen on 2007-05-07
> 
# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x -0
gap_y -0


Have you tried fiddling w/ these?  Seems like I changed these to get my older conky outputs to go flush into a corner.  Not sure, you may want to ask the guys in #conky on freenode, they've helped me too many times. =]

---

