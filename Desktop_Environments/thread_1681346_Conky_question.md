---
title: "Conky question"
date: 2011-02-04
forum: Desktop Environments
---

### Post by Arminius on 2011-02-04
here's the whole code ```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
#

# Create own window instead of using desktop (required in nautilus)
# own_window yes
# own_window_type override
background no
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont LiberationSans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5
# maximum_width 300

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 0

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color e5e5e5
color0 66cccc # 'header' color

own_window_colour brown

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 20
gap_y 30

# Rounded corners and 'transparency' w/cairo
lua_load ~/.conky/draw_bg.lua
lua_draw_hook_pre draw_bg

#${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
# ********************************************************************************* #
# stuff after 'TEXT' will be formatted on screen
TEXT



$color0${font UbuntuTitleBold:size=9}${exec whoami}@$nodename${font} ${hr 2}$color${voffset -65}${offset -130}${font OpenLogos:size=80}v${font}$color
${voffset -20}Ubuntu: 10.10 "Maverick Meerkat"
Kernel: $kernel
Uptime: $uptime
Updates Available: ${execi 1200 aptitude search "~U" | wc -l | tail}

$color0${font UbuntuTitleBold:size=9}CPU${font} ${hr 2}$color
${freq}MHz   Load: ${loadavg}
${font StyleBats:size=15}${font}CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 6,248}
${font StyleBats:size=15}${font}CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 6,248}

NAME${alignr 9}PID     CPU%   MEM%
${top name 1}${alignr 9}${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2}${alignr 9}${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3}${alignr 9}${top pid 3}   ${top cpu 3}    ${top mem 3}

$color0${font UbuntuTitleBold:size=9}MEMORY${font} ${hr 2}$color
RAM:   $memperc%   ${alignr}${membar 6,220}$color
Swap:  $swapperc%   ${alignr}${swapbar 6,220}$color

NAME${alignr 9}PID     CPU%   MEM%
${top_mem name 1}${alignr 9}${top_mem pid 1}   ${top_mem cpu 1}    ${top_mem mem 1}
${top_mem name 2}${alignr 9}${top_mem pid 2}   ${top_mem cpu 2}    ${top_mem mem 2}
${top_mem name 3}${alignr 9}${top_mem pid 3}   ${top_mem cpu 3}    ${top_mem mem 3}

$color0${font UbuntuTitleBold:size=9}DISK${font} ${hr 2}$color
Root:  ${fs_used_perc /}%   ${alignr}${fs_bar 6,246 /}$color
Ext Videos:  ${fs_used_perc /media/Ext Videos}%   ${alignr}${fs_bar 6,219 /media/Ext Videos}$color
Ext VID1.5:  ${fs_used_perc /media/Ext VID1.5}%   ${alignr}${fs_bar 6,218 /media/Ext VID1.5}$color
Ext Backup1:  ${fs_used_perc /media/Ext Backup1}%   ${alignr}${fs_bar 6,210 /media/Ext Backup1}$color
Internal Video:  ${fs_used_perc /media/INTERNAL VI}%   ${alignr}${fs_bar 6,203 /media/INTERNAL VI}$color
${diskiograph 555753 eeeeec}

##################
##   NETWORK    ##
##################
${voffset 6}${font WenQuanYiMicroHei:bold:size=8.75}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}a${font}${color6}${offset 5}Private${offset 3}IP${alignr}${addr eth0}
${font PizzaDudeBullets:size=10}${color2}a${font}${color6}${offset 5}Public${offset 7}IP${alignr}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}T${font}${color6}${offset 5}Down${alignr}${downspeed eth0}
${font PizzaDudeBullets:size=10}${color2}N${font}${color6}${offset 5}Up${alignr}${upspeed eth0}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}T${font}${color6}${offset 5}Downloaded${alignr}${totaldown eth0}
${font PizzaDudeBullets:size=10}${color2}N${font}${color6}${offset 5}Uploaded${alignr}${totalup eth0}
```

and the part I'm having problems with is at the bottom, here ```
##################
##   NETWORK    ##
##################
${voffset 6}${font WenQuanYiMicroHei:bold:size=8.75}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}a${font}${color6}${offset 5}Private${offset 3}IP${alignr}${addr eth0}
${font PizzaDudeBullets:size=10}${color2}a${font}${color6}${offset 5}Public${offset 7}IP${alignr}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}T${font}${color6}${offset 5}Down${alignr}${downspeed eth0}
${font PizzaDudeBullets:size=10}${color2}N${font}${color6}${offset 5}Up${alignr}${upspeed eth0}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}T${font}${color6}${offset 5}Downloaded${alignr}${totaldown eth0}
${font PizzaDudeBullets:size=10}${color2}N${font}${color6}${offset 5}Uploaded${alignr}${totalup eth0}
```

Down, Up, Downloaded and Uploaded just display 0B, and they never change.

Anyone got any ideas on how to fix that?

---

### Post by Brandon Williams on 2011-02-05
Is eth0 the correct interface? If it's a wireless interface, it's more likely to be eth1 or wlan0. Run 'ip addr show | grep "state UP"' on the command line. What interface name is listed?

---

