---
title: "Conky Help"
date: 2009-07-23
forum: Desktop Environments
---

### Post by djantz on 2009-07-23
Anyone know how to make acpitemp show up as Fahrenheit instead of Celsius? It won't let me do acpitempf. Or add a little function at the end so it multiplies by 9, divides by 5, adds 32. 

I also can't seem to get the Icons next to the HDD to show. 
Any help is much appreciated.

[INDENT][INDENT][PHP]# Use Xft?
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
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 200

# Draw shades?
draw_shades no

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
#default_outline_color grey
own_window_colour grey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 35

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
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
${color #009bf9}SYSTEM ${hr 2}
${alignc 17}${color white}${font Arial Black:size=16}david${font}
${alignc}Maybe it's not my weekend
${alignc}But it's gonna be my year
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font}   CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font Webdings:size=16}~${font}  Battery: ${battery_percent BAT0}% ${alignr}${battery_bar 8,60 BAT0}
${alignc}Processes: ${processes}   Running: ${running_processes}

${color #009bf9}DATE ${hr 2}
${alignc 17}${color white}${font Arial Black:size=16}${time %H:%M}${font}
${alignc}${time %A %d %B %Y}

${color #009bf9}HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Linux:
${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Vista:
${voffset 4}${fs_used /media/Vista}/${fs_size /media/Vista} ${alignr}${fs_bar 8,60 /media/Vista}

${color #009bf9}WEATHER ${hr 2}
${alignc}${color whitesmoke}${execi 1680 python /home/david/.scripts/conkyForecast.py --location=USCA0632 --datatype=CN --refetch}
Conditions:${offset 4}${execi 1680 python /home/david/.scripts/conkyForecast.py --location=USCA0632 --datatype=CT}
Temperature: ${execi 1680 python /home/david/.scripts/conkyForecast.py --location=USCA0632 --datatype=HT --imperial}
Windspeed:${execi 1680 python /home/david/.scripts/conkyForecast.py --location=USCA0632 --datatype=WS --imperial} ${execi 1680 python /home/david/.scripts/conkyForecast.py --location=USCA0632 --datatype=WD}
Humidity: ${execi 1680 python /home/david/.scripts/conkyForecast.py --location=USCA0632 --datatype=HM}
${alignr}${voffset -60}${offset -70}${font Weather:size=54}${execi 1680 python /home/david/.scripts/conkyForecast.py --location=USCA0632 --datatype=WF}${font}

${color #009bf9}MAIL ${hr 2}
${alignc}dcjantz@gmail.com
${alignc}${color #009bf9}${texeci 120 python ~/.scripts/gmail.py}

${color white}TEMP ${hr 2}
${color white} CPU: ${alignr}${acpitemp}C$color
 GPU: $alignr ${execi 30 nvidia-settings -q [gpu:0]/GPUCoreTemp | grep '):' | awk '{print $4}' | sed 's/\.//'}C


${color #009bf9}NETWORK ${hr 2}
${alignc}${color white}${addr eth1}
Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color #009bf9}MUSIC ${hr 2}
${color white}${alignc}${if_running audacious}${exec audtool --current-song}
${execbar expr 100 \* $(audtool --current-song-output-length-seconds) \/ $(audtool --current-song-length-seconds)}$endif
${alignr}${exec audtool --current-song-length} [/PHP][/INDENT][/INDENT]

---

### Post by Crunchy the Headcrab on 2009-07-25
Lots of good help here. [http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+time")

---

