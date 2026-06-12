---
title: "Problem: HD info and CowThink in Conkyrc"
date: 2009-02-02
forum: General Help
---

### Post by itang sanjana on 2009-02-02
Hello guys,

I have 2 problems here.

1) could someone enlight me about this error:
```
Conky: statfs '/media/disk': No such file or directory
Conky: statfs '/media/disk-1': No such file or directory
Conky: $endif: no matching $if_*
Conky: desktop window (10000bb) is subwindow of root window (5c)
Conky: window type - override
Conky: drawing to created window (3800001)
Conky: drawing to double buffer
```

2) I try to run CowThink under Conky, but I just can't seems to ask this Cow to pose correctly:D
See the picture for detail. Any hint how to fix this?

Thanks.

Here is the code
```

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 200
#maximum_width 0

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color white
own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 15
gap_y 35

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
  ${color lightblue}${font OpenLogos:size=60}u${font}
${color lightblue}SYSTEM ${hr 2}${color lightblue}
${voffset 2}${font OpenLogos:size=25}u${font} Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}x${font}   Machine:  ${alignr}${machine}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font}   CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}

${font StyleBats:size=16}z${font}   Highest MEM $alignr CPU% MEM%
${hr 1}
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${color lightblue}HD ${hr 2}${color lightblue}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:
${voffset 4}${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}D:
${voffset 4}${fs_free /media/disk}/${fs_size /media/disk} ${alignr}${fs_bar 8,60 /media/disk}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}E:
${voffset 4}${fs_free /media/disk-1}/${fs_size /media/disk-1} ${alignr}${fs_bar 8,60 /media/disk-1}

${color lightblue}CowThink ${hr 2}${color lightblue}
${execi 1000 cowthink -s 'XOXO'}

${endif}


```

---

### Post by chamber on 2009-02-02
I would check the properties of those 2 disks just to confirm the names on them.

---

