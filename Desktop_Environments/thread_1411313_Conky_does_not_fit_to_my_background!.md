---
title: "Conky does not fit to my background!"
date: 2010-02-19
forum: Desktop Environments
---

### Post by vickoxy on 2010-02-19
I try to change my background, but most of the pictures and conky won´t cooperate.
See bellow:
What to do?

I tried to save jpeg in png-but no change...

my conkyrc:
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes


# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 210 0
maximum_width 210 0

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
use_xft yes
xftfont Mono:size=7
xftalpha 0.8
text_buffer_size 2048

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3



# Default colors and also border colors, grey90 == #bdd3ff
default_color ffffff

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 20


#${color blue}FORTUNE ${hr 2}$color
#${execi 120 fortune -s | fold -w50}


#${color blue}LOGGING ${hr 2}$color
#${execi 30 tail -n3 /var/log/messages | fold -w50}



# stuff after 'TEXT' will be formatted on screen

TEXT
${font Arial:size=26}${alignc}${time %H:%M:%S}${font}
${alignc}${time %A, %d.%m.%Y}
${color #ffffff}${hr 2}$color
${execpi 300 cal | sed -e 's/'`date | awk '{print $3}'`'/\$\{color e84448}'`date | awk '{print $3}'`'\$\{color}/'|sed 's/^/${alignc}/'}
${voffset -20}${color #ffffff}SYSTEM ${hr 2}$color
${voffset 4}UpTime: ${alignr}${color }$uptime
${voffset 2}Kern: ${alignr}$kernel
${voffset 2}CPU: ${cpu}% ${alignr 1}${cpubar 6,80}
${cpugraph 000000 ffffff}
Intel Atom N270 ${alignr} ${alignr}${freq}MHz   ${acpitemp}C
${voffset 2}HDD Temp${alignr}${hddtemp /dev/sda localhost 7634}C
${voffset 2}RAM: $memperc% ${alignc} $mem${alignr 7} ${membar 6,80}
${voffset 2}${alignc -44}CPU%	${alignr}MEM%
${voffset 2}${top_mem name 1}${alignr}${top_mem cpu 1}   ${top_mem mem 1}
${voffset 2}${top_mem name 2}${alignr}${top_mem cpu 2}   ${top_mem mem 2}
${voffset 2}${top_mem name 3}${alignr}${top_mem cpu 3}   ${top_mem mem 3}
${voffset 2}${top_mem name 4}${alignr}${top_mem cpu 4}   ${top_mem mem 4}
${voffset 6}${color #ffffff}STORAGE ${hr 2}$color
${voffset 2}HD: ${voffset 0}${fs_free /home}/${fs_size /home} ${alignr 1}${fs_bar 6,50 /home}
${if_mounted /media/DATA}${voffset 2}SD/USB: ${voffset 0}${fs_free /media/DATA}/${fs_size /media/DATA} ${alignr}${fs_bar 6,50 /media/DATA}${endif}
${color #ffffff}NETWORK ${hr 2}$color
${voffset 2}Upload: ${alignr}${upspeedf eth2} KB/s
${voffset 2}Download: ${alignr}${downspeedf eth2} KB/s
```

---

### Post by vickoxy on 2010-02-20
I will mark this thread as solved, because applying new theme solved the issue.

---

