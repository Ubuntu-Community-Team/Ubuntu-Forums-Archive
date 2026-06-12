---
title: "Need help with Conky"
date: 2009-04-21
forum: General Help
---

### Post by JECHO on 2009-04-21
Hey guys I have been using conky for a while now and once i installed jaunty all of a sudden my conkyrc isn't working how it used to. It used to run perfectly on the desktop (on intrepid) and now it has a background glow and doesn't go transparent when i use the compiz cube... here is my conkyrc and attached are screenshots of my issue. Any help is appreciated. 

Thanks

```
# UBUNTU-CONKY
# A comprehensive conky script, configugold for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat connections to your computer
#

# Create own window instead of using desktop (requigold in nautilus)
own_window yes
own_window_type dock
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (golduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 5.0

# Minimum size of text area
# minimum_size 250 4

minimum_size 280
maximum_width 280

# Draw shades?
draw_shades no

# Text stuff
draw_outline no
# amplifies text if yes
draw_borders no
# font sans
uppercase no
# set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 5

# border width
border_width 2b0

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 15
gap_y 30

# Antialiased Fonts
# use_xft
# xftfont Sans
# font size 2

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color red}SYSTEM ${hr 2}$color

$alignc Ubuntu running on $machine
$alignc Kernel: ${kernel}
$alignc Uptime: ${uptime}
$alignc Host: ${nodename}

${color red}CPU ${hr 2}$color

Usage: ${cpu}% of ${freq} MHz $alignr${cpubar 6,120}

${cpugraph 25,280 000000 bd0000}

${color red}PROCESSES ${hr 2}${color}

NAME             PID       CPU%      MEM%
${color a2a2a2}${hr}$color
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${top name 5} ${top pid 5}   ${top cpu 5}    ${top mem 5}

${color red}MEMORY ${hr 2}$color

Memory	 used ${mem} of ${memmax}

RAM $memperc % ${membar 6,60}$color ${alignr}Swap $swapperc%   ${swapbar 6,60}$color

$alignr${memgraph 25,280 3d3400 cdae00}

${color red}DISK ${hr 2}$color

Root:   ${fs_used_perc /}%${alignr}${color ac0000}${fs_bar 6,195 /}$color4
Home:   ${fs_used_perc /home}%${alignr}${color ac5100}${fs_bar 6,195 /home}$color
Usr:    ${fs_used_perc /usr}%${alignr}${color ac7d00}${fs_bar 6,195 /usr}$color
Var:    ${fs_used_perc /var}%${alignr}${color acaa00}${fs_bar 6,195 /var}$color

${color red}Windows :$color

Progz:  ${fs_used_perc /media/Progz}%${alignr}${color 760000}${fs_bar 6,195 /media/Progz}$color
Down:   ${fs_used_perc /media/Down}%${alignr}${color 763800}${fs_bar 6,195 /media/Down}$color
Media:  ${fs_used_perc /media/Media}%${alignr}${color 765600}${fs_bar 6,195 /media/Media}$color
Filmz:  ${fs_used_perc /media/Filmz}%${alignr}${color 767500}${fs_bar 6,195 /media/Filmz}$color

${color red}NETWORK (${addr eth0}) ${hr 2}$color

       Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s   
$color${downspeedgraph eth0 25,135 000000 1d9a00} ${alignr}${upspeedgraph 
eth0 25,135 000000 03a3ff}       $color
Total: ${color 1d9a00}${totaldown eth0}${color }${alignr}Total: ${color 03a3ff}${totalup eth0}  $color

Inbound: ${tcp_portmon 1 32767 count}    Outbound: ${tcp_portmon 32768 61000 count}${alignr}    Ttorrent: ${tcp_portmon 6881 6999 count}
Total: ${tcp_portmon 1 65535 count} 

```

---

### Post by codeseer on 2009-04-21
try adding:

```
background yes
```

---

