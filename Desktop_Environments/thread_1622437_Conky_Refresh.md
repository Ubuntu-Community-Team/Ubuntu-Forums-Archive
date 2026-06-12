---
title: "Conky Refresh"
date: 2010-11-15
forum: Desktop Environments
---

### Post by Frogs Hair on 2010-11-15
I have been thinking about installing Conky because there are some nice configurations available. I installed (all features enabled) version from software center to check it out before trying to install a custom configuration. I noticed when the graphs refresh it is choppy and tends to flash a bit to the point of being annoying. Is this normal ? My visual effects are set to normal. Ubuntu 10.10 not Lubuntu.

---

### Post by mcduck on 2010-11-15
Do you have "double_buffer" enabled in your Conky configuration? If not, try enabling it.

---

### Post by ajgreeny on 2010-11-15
You may need to add the lines
```
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
``` to your **.conkyrc** file in your home folder.  It can possibly overcome this problem, though as you can see from the comment, it does not always work.

If you don't have a personal **.conkyrc** in your home, but are just using the example that comes with conky when installed, get a few template **.conkyrc** files to try and then edit the one that works best to make your own version.

As a start, here's mine; see how that works for you with appropriate edits to your system.

```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=10

# Text alpha when using Xft
xftalpha 0.9

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 220

# Maximum width
maximum_width 220

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
# stippled_borders 8

# border margins
# border_margin 2

# border width
# border_width 1

# Default colors and also border colors
default_color white
default_shade_color red
default_outline_color green

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen

TEXT
${font Trebuchet MS:size=30} ${alignc}${time %k:%M}
${font Trebuchet MS:size=20} ${alignc}${time %a %b %d %Y}${font Trebuchet MS:size=10}

${color #56073D}Hostname:${color #DE0084}$alignr$nodename
${color #56073D}Uptime:${color #DE0084}$alignr$uptime

${color #56073D}CPU ${color #DE0084}${cpu cpu1}% ${color #56073D}${cpubar cpu1}
${color #56073D}Processes: ${color #DE0084}$processes ${alignr}Running: $running_processes
#
#${color #56073D}CPU Usage        ${color #DE0084} $alignr PID   CPU%   MEM%
#${color #56073D} ${top name 1} ${color #DE0084} $alignr ${top pid 1}  ${top cpu 1}  ${top mem 1}

${color #56073D}sda1
${color #56073D} Root ${color #DE0084}${fs_used_perc /}% ${color #56073D}${fs_bar /}
$alignr ${color #DE0084}${fs_used /}/${fs_size /}
${color #56073D}sda2
${color #56073D} Home ${color #DE0084}${fs_used_perc /home}% ${color #56073D}${fs_bar /home}
$alignr ${color #DE0084}${fs_used /home}/${fs_size /home}

${color #56073D}RAM Usage:
$alignr${color #DE0084}$mem of $memmax ${color #DE0084}= ${color #DE0084}$memperc%  

${color #56073D}Swap: ${color #DE0084}$swapperc% ${color #56073D}${swapbar}
${color #DE0084} ${alignr}$swap of $swapmax

${color #56073D}NETWORK IP:${color #DE0084} $alignr eth0 -  ${color #DE0084}${addr eth0}

${color #56073D}DOWN:${color #DE0084} ${downspeed eth0}/s ${color #56073D}$alignr TOTAL ${color #DE0084}${totaldown eth0}
${color #56073D}${downspeedgraph eth0 30,220 000000 #56073D}

${color #56073D} Up:${color #DE0084} ${upspeed eth0}/s ${color #56073D}$alignr TOTAL ${color #DE0084}${totalup eth0}
${color #56073D}${upspeedgraph eth0 30,220 000000 #56073D}
```

---

### Post by Frogs Hair on 2010-11-15
No I didn't , the terminal reads Conky:drawing to single buffer

---

### Post by Frogs Hair on 2010-11-15
Thanks ajgreeny I will give it a try:)

---

