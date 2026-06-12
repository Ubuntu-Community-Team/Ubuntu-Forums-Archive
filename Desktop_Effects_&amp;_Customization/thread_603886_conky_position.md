---
title: "conky position"
date: 2007-11-05
forum: Desktop Effects &amp; Customization
---

### Post by NuK3 on 2007-11-05
Hey, I just found a ~/.conkyrc file I liked, but the problem is that it is in the lower right side of the screen.  How would I edit the conkyrc file to get it in the top left part of the screen?  Here is my ~/.conkyrc file:

```
# Create own window instead of using desktop (required in nautilus)
# Note that own_window_type is set to normal so that it will run on fluxbox; default is override
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 275 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font -*-dejavu sans-medium-*-*-*-9-*-*-*-*-*-*-*
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen
TEXT
$color
${time %A %B %e}     Uptime: $uptime
${time %I:%M %p}
${if_running audacious}
${color orange}Audacious ${hr 2}$color
${exec audtool --current-song}
${exec audtool --current-song-output-length} / ${exec audtool --current-song-length}
$endif
${color orange}CPU ${hr 2}$color
${cpu}% at ${freq} MHz ${alignr}Temp: ${acpitemp}C
${cpugraph 000000 ffffff}
Processes: ${processes} ${alignr}Running: ${running_processes}

Name              ${alignr}CPU%  MEM%
${top name 1}   ${alignr}${top cpu 1}    ${top mem 1}
${top name 2}   ${alignr}${top cpu 2}    ${top mem 2}
${top name 3}   ${alignr}${top cpu 3}    ${top mem 3}
${top name 4}   ${alignr}${top cpu 4}    ${top mem 4}

RAM:   $memperc%   ${membar 6}$color

${color orange}Ethernet (68.118.239.165) ${hr 2}$color
Down: $color${downspeed eth0} kb/s  Total: ${totaldown eth0}
Up: ${upspeed eth0} kb/s       Total: ${totalup eth0}

${color orange}Weather ${hr 2}$color
${execi 300 /home/someone/weather.sh}
```

---

### Post by fedex1993 on 2007-11-05
i thinks it has to do with ```
# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
```

---

### Post by tadada on 2007-11-05
yes that is the correct lines uncomment the line that contains the area where you want it then comment in the bottom right line then restart conky

---

