---
title: "Conky falls into deep sleep with USB mount."
date: 2011-05-01
forum: Desktop Environments
---

### Post by ulabunt on 2011-05-01
Hi
I'm experiencing low importance nuisance with conky.
I'm running ubuntu 10.10 and use conky to have basic system overview. 
Whenever I mount/umount USB flash, conky disapears from display. It does not crash, it only falls into neverending sleep (process state: Sl+). When I send rehub signal (kill 1 {conky_pid}) conky happily wake up, reloads configuration and shows me what I want to see. I dont have anything USB realted in my monitor. Any ideas?
Thanks. V.

---

### Post by ulabunt on 2011-06-01
Alright its not just USB mount that makes conky sleep. It falls into sleep quite often for various reason.
I'm sure number of people is experiencing this behavior.. but since nobody is responding.. it looks like the most time effective answer is to say good bye to conky.

---

### Post by stinkeye on 2011-06-01
Don't have that behaviour and haven't heard of it before.
Would help if you posted your conky config.

---

### Post by ulabunt on 2011-12-09
Its just happening all the time vanishes from the desktop and goes to sleep.  I dont like conky. One of the disks are mounted via NFS. 

config:
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type desktop 
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 2.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders yes
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 0
 
# border margins
border_margin 1
 
# border width
border_width 1
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color grey90
 
own_window_colour brown
own_window_transparent yes
 
# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
 
# Gap between borders of screen and text
gap_x 10
gap_y 35
 
#top name with
#top_name_width 15

# stuff after 'TEXT' will be formatted on screen

TEXT
#$color
#${color #D28E47}SYSTEM ${hr 2}$color
#$nodename $sysname $kernel on $machine
${color orange}CPU ${hr 2}$color
Freq: ${freq}MHz     ${alignr}Load: ${cpu cpu}%
#${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
#$cpubar
${cpugraph 000000 ffffff}
#CPU1:${cpu cpu0}% ${freq cpu1}MHz CPU2:${cpu cpu1}% ${freq cpu2}MHz
#CPU1:${cpu cpu0}%  ${alignr}CPU2:${cpu cpu1}%
#${cpugraph cpu0 25,100 000000 ffffff}${alignr}${cpugraph cpu1 25,100 000000 ffffff} 
#NAME             PID       CPU%      MEM%
#${top name 1}  ${top pid 1}   ${top cpu 1}    ${top mem 1}
#${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
#${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
#${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${color orange}MEMORY ${hr 2}$color
RAM  :   $memperc%   ${alignr}${membar 6,120}$color
Swap:  $swapperc%   ${alignr}${swapbar 6, 120}$color
 
${color orange}DISK ${hr 2}$color
root        : ${fs_used_perc /}%  ${alignr}${fs_bar 6,120 /}$color 
kubuntu: ${fs_used_perc /kubuntu}%  ${alignr}${fs_bar 6,120 /kubuntu}$color 
space    : ${fs_used_perc /space}%  ${alignr}${fs_bar 6,120 /space}$color 
storage : ${fs_used_perc /storage}%  ${alignr}${fs_bar 6,120 /storage}$color 
 
${color orange}NETWORK (${addr wlan0}) ${hr 2}$color
Down: $color${downspeed wlan0} ${alignr}Up: ${upspeed wlan0}
${downspeedgraph wlan0 25,100 000000 ff0000} ${alignr}${upspeedgraph wlan0 
25,100 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
#${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
#${color orange}LOGGING ${hr 2}$color
#${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
#${color orange}FORTUNE ${hr 2}$color
#${execi 120 fortune -s | fold -w50}

---

### Post by stinkeye on 2011-12-09
Change
```
own_window_type desktop
```
to 
```
own_window_type normal
```
or
```
own_window_type override
```

---

