---
title: "conky/beryl question"
date: 2007-09-24
forum: Desktop Effects &amp; Customization
---

### Post by timzak on 2007-09-24
I have conky set to load 10 seconds after startup.  This eliminated the conky disappearing bug that has been asked many times before here.  However, I notice that when I activate the beryl cube, conky does not become transparent with the rest of the desktop.  Is it possible for conky to be transparent along with the rest of my desktop when I activate the cube?

Thanks.

---

### Post by timzak on 2007-09-26
*bump*

Just want to know if conky can be made transparent when I activate the beryl cube.  Currently, my whole desktop is transparent during the spinning cube, except for conky.

Thank you.

---

### Post by notwen on 2007-09-26
Could you copy/paste your conkyrc here?

---

### Post by timzak on 2007-09-28
> **notwen said:**
> Could you copy/paste your conkyrc here?

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
#own_window_hints undecorated,below,skip_taskbar
#own_window_type desktop
#own_window_colour brown
own_window_transparent yes
own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

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



# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kernel: ${color }$kernel
${offset 240}${color slate grey}Proc: ${color }Intel Core2 Duo E4300
${offset 240}${color slate grey}Freq: ${color }${freq_g} Ghz  ${i2c 9191-0290 fan 2} RPM
${offset 240}${color slate grey}CPU Temp: ${color }${i2c 9191-0290 temp 2} C 
${offset 240}${color slate grey}Sys Temp: ${color }${i2c 9191-0290 temp 1} C
${offset 240}${color slate grey}Core1 Usage: ${color } ${cpu cpu1}%
${offset 240}${cpubar cpu1}
${offset 240}${color slate grey}Core2 Usage: ${color } ${cpu cpu2}%  
${offset 240}${cpubar cpu2}
${offset 240}${color slate grey}Total Processes: ${color }$processes  
${offset 240}${color slate grey}Active Processes:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU Processes:
${offset 240}${color #ddaa00} ${top name 1}${top cpu 1} %
${offset 240}${color lightgrey} ${top name 2}${top cpu 2} %
${offset 240}${color lightgrey} ${top name 3}${top cpu 3} %

${offset 240}${color slate grey}Highest MEM Processes:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1} %
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2} %
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3} %
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4} %
${offset 240}${color lightgrey} ${top_mem name 5}${top_mem mem 5} %

${offset 240}${color slate grey}MEM in use:  ${color } $memperc% 
${offset 240}$mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP in use:  ${color }$swapperc% 
${offset 240}$swap/$swapmax
${offset 240}${swapbar 3,100}
${offset 240}${color slate grey}HOME Dir:  ${color }${fs_free_perc /home}%  free 
${offset 240}${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}NETWORK Throughput: 
${offset 240}${color}Upload: ${color }${upspeed eth0} KB/sec
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Download: ${color }${downspeed eth0}KB/sec${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}
```

---

### Post by timzak on 2007-09-30
*bump*

---

### Post by Rupertronco on 2007-09-30
Change:

own_window_type root

to

own_window_type override

---

### Post by timzak on 2007-09-30
Thank you, Rupertronco!  That worked perfectly.

I really appreciate your help.  :)

Best Regards.

---

