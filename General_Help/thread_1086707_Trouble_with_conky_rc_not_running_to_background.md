---
title: "Trouble with conky rc not running to background"
date: 2009-03-04
forum: General Help
---

### Post by Nano_ext3 on 2009-03-04
Hi, installed conkrc, and when run, even though set to background runs in its own window.  Help?  A fault on the part of composite window manager?

rc file:


# Use Xft?
use_xft yes
xftfont Tlwgmono:size=7.4:bold
xftalpha 1
text_buffer_size 2048


# set to yes if you want Conky to be forked in the background
background yes

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 200 0
maximum_width 200

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
default_color FFFFFF
#default_shade_color white
#default_outline_color black
#own_window_colour 000000

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 50

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






DATE ${hr 1}
${alignc 30}${font Freemono:size=22:bold}${time %H:%M}${font}

${alignc}${time %a %d %b %Y}

SYS ${hr 1}

${alignc}Xubuntu Linux 8.10 Intrepid Ibex

Kernel  ${alignr}${kernel}
CPU1 ${freq_dyn_g 1} GHz ${alignr}${cpu cpu1}%  ${cpubar cpu1 5,75}
CPU2 ${freq_dyn_g 2} GHz ${alignr}${cpu cpu2}%  ${cpubar cpu2 5,75}
RAM ${alignr}$memperc%  ${membar 5,75}
SWAP ${alignr}$swapperc%  ${swapbar 5,75}
Uptime ${alignr}${uptime}

HDD ${hr 1}

Filesystem ${alignr}${fs_used /}/${fs_size /}
   ${alignr}${fs_used_perc /}%  ${fs_bar 5,120 /}
Western Digital ${alignr}${fs_used /media/Tera}/${fs_size /media/Tera}
${alignr}${fs_used_perc /media/Tera}% ${fs_bar 5,120 /media/Tera} 

NET ${hr 1}
${if_existing /proc/net/route wlan0}
Up     ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 5,75 000000 000000}
Down   ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 5,75 000000 000000}
Upload ${alignr}${totalup wlan0}
Download ${alignr}${totaldown wlan0}
Signal ${alignr}${wireless_link_qual wlan0}% ${wireless_link_bar 5,75 wlan0}
Local Ip ${alignr}${addr wlan0}
Public Ip ${alignr}${execi 1 ~/.scripts/ip.sh}
${else}${if_existing /proc/net/route eth0}
Up     ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 5,75 000000 000000}
Down   ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 5,75 000000 000000}
Local Ip ${alignr}${addr eth0}
Public Ip ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}
Network Unavailable
${endif}

---

