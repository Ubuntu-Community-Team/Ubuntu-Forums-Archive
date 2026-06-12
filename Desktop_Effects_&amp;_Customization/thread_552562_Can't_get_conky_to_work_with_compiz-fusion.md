---
title: "Can't get conky to work with compiz-fusion"
date: 2007-09-16
forum: Desktop Effects &amp; Customization
---

### Post by Nythain on 2007-09-16
i for the life of me cant get conky to work with compiz fusion
i wait till after compiz loads, and emerald... then if i try to run conky (either by script or terminal or alt+f2) it shows up as a black box and laggs my system to near death.
here is my conkyrc file wich worked fine when i was running fluxbox
```

# conky configuration

# set to yes if you want Conky to be forked in the background
background no

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont DejaVu Sans Mono:pixelsize=12

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
#own_window_type override
#own_window_type default
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 398 450
maximum_width 398

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 878
gap_y 30

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders yes

# Stippled borders?
stippled_borders 0

# border margins
#border_margin 5

# border width
border_width 1

# Default colors and also border colors
#default_color A29F84
default_color black
default_shade_color white
default_outline_color black

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

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
use_spacer no

#${color }Connections: ${alignr}Service/Port:
#${tcp_portmon 1 65535 rhost 0} ${alignr} ${tcp_portmon 1 65535 rservice 0}
#${tcp_portmon 1 65535 rhost 1} ${alignr} ${tcp_portmon 1 65535 rservice 1}
#${tcp_portmon 1 65535 rhost 2} ${alignr} ${tcp_portmon 1 65535 rservice 2}
#${tcp_portmon 1 65535 rhost 3} ${alignr} ${tcp_portmon 1 65535 rservice 3}
#${tcp_portmon 1 65535 rhost 4} ${alignr} ${tcp_portmon 1 65535 rservice 4}
#${tcp_portmon 1 65535 rhost 5} ${alignr} ${tcp_portmon 1 65535 rservice 5}

#${font :size=14}${color }Weather ${hr}$font
#${execi 600 /home/rune/.conky/scripts/weather/weather.sh 64118}

TEXT
${font :size=18}${time %A %B %d}${alignr}${time %I:%M %P}$font
$color
${font :size=14}${color }System ${hr}$font
${color }rune@$nodename - $sysname $kernel on $machine
${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} using ${cpu}% on $running_processes process.
${cpugraph 20,395 000000 000000}
${alignc}${color }Averaging $loadavg Load.
${font :size=14}${color }Disks ${hr}$font
${color }DISK IO: ${alignc}$diskio
${diskiograph 20,395 000000 000000}
${color }ROOT: ${alignc}${fs_used /} of ${fs_size /} used. ${fs_free_perc /} % Free ${fs_free /}
${fs_bar 5,395 /}
${color }Data: ${alignc}${fs_used /data} of ${fs_size /data} used. ${fs_free_perc /data}% Free ${fs_free /data}
${fs_bar 5,395 /data}
${color }Video: ${alignc}${fs_used /data/video} of ${fs_size 
/data/video} used. ${fs_free_perc /data/video}% Free ${fs_free 
/data/video}
${fs_bar 5,395 /data/video}
${font :size=14}${color }Net ${hr}$font
${alignc}${addr ra0}
${color }Up: ${color }${upspeed ra0} k/s${alignr}${color}Down: ${color }${alignr}${downspeed ra0}k/s
${upspeedgraph ra0 20,195 000000 000000}${alignr}${downspeedgraph ra0 20,195 000000 000000}
${color }Inbound: ${tcp_portmon 1 32767 count}${alignr}Outbound: ${tcp_portmon 32768 61000 count}

```
im thinkin it might have to do with the own window and window types, but im not sure... any ideas, anyone else have this problem

just so you know, yes i have dbe loaded in xorg.conf and im running kde if that matter

---

### Post by Nythain on 2007-09-16
no one has had this problem ??? just call me the most unique person in teh world, seems like every problem i've encountered lately just doesnt exist

---

### Post by RedSquirrel on 2007-09-17
I haven't tried compiz-fusion, but have you tried different settings for own_window_type (**normal**, for example)?

---

### Post by vold on 2007-09-21
Mine wasn't working either, but I have neither Gnome nor KDE installed so the symptoms were different.
Anyway, the lines I changed in .conkyrc were the own_window ones, it is now:

> own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

The only real difference I can see from yours in the 
> own_window_type normal

Other than that there isnt really anything in yours that isnt in mine, except

> # Update interval in seconds
update_interval 1.0

Mine is 5.0. Less updates, less cpu.

Conky is now sitting on the right hand side of my display, with weather, rss feed, mpd, top cpu, top mem, netwok up and down graphs, wlan status and bar, ram (and graph), cpu usage (and graph) and the time and using no cpu really. Im running compiz-fusion in gutsy, with avant-window-manager and nothing else. So it could be a kde thing for you.

---

### Post by daimaru on 2007-10-27
edit : 

nevermind i found the solution to conky always staying on top 

[http://www.uluga.ubuntuforums.org/showthread.php?t=388560&highlight=conky+always+on+top]("http://www.uluga.ubuntuforums.org/showthread.php?t=388560&highlight=conky+always+on+top")

---

