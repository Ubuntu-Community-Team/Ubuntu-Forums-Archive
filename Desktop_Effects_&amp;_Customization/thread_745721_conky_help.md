---
title: "conky help"
date: 2008-04-04
forum: Desktop Effects &amp; Customization
---

### Post by Rylin on 2008-04-04
I recently installed conky and even pasted in custom conky script text. For some reason it runs as a window instead of 'embedding' itself as part of the desktop. Wondering if someone could help me fix this and also what to paste in to get those custom looks everyone is using.

Using Ubuntu Gutsy w/ gnome desktop if that matters or not either.

Thanks ;)

```
# set to yes if you want Conky to be forked in the background
background yes

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Create own window instead of using desktop (required in nautilus)
own_window no
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

#own_window no
#own_window_transparent yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Liberation Mono Italic:size=8

uppercase yes

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 10

# border margins
border_margin 4

# border width
border_width 1

# Text alignment, other possible values are commented
#minimum_size 10 10
gap_x 13
gap_y 45
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

# Subtract file system buffers from used memory?
no_buffers yes

 
TEXT
${alignc}${color #EB5B08}$sysname kernel $kernel 
${alignc}${color #EB5B08}${exec cat /etc/issue.net} on $machine host $nodename

${color #EB5B08}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color #EBA713} ${freq_dyn}Mhz
${color #EB5B08}Current CPU usage & temp:${color #EBA713}  ${cpu}%${color #EB5B08}, ${color #EBA713}${acpitemp}C ${color #EB5B08}/${color #EBA713} ${acpitempf}F

${color #EB5B08}Load average:${color #EBA713}   $loadavg

${color #EB5B08}CPU usage         ${alignr}PID     CPU%   MEM%
${color #EBA713} ${top name 1}${alignr}${top pid 1}   ${top cpu 1}   ${top mem 1}
${color #EBA713} ${top name 2}${alignr}${top pid 2}   ${top cpu 2}   ${top mem 2}
${color #EBA713} ${top name 3}${alignr}${top pid 3}   ${top cpu 3}   ${top mem 3}
${color #EBA713} ${top name 4}${alignr}${top pid 4}   ${top cpu 4}   ${top mem 4}
${color #EBA713} ${top name 5}${alignr}${top pid 5}   ${top cpu 5}   ${top mem 5}

${color #EB5B08}Mem usage
${color #EBA713} ${top_mem name 1}${alignr}${top_mem pid 1}   ${top_mem cpu 1}   ${top_mem mem 1}
${color #EBA713} ${top_mem name 2}${alignr}${top_mem pid 2}   ${top_mem cpu 2}   ${top_mem mem 2}
${color #EBA713} ${top_mem name 3}${alignr}${top_mem pid 3}   ${top_mem cpu 3}   ${top_mem mem 3}

${color #EB5B08}RAM Usage:${color #EBA713} $mem/$memmax - $memperc% $membar

${color #EB5B08}Swap Usage:${color #EBA713} $swap/$swapmax - $swapperc% ${swapbar}

${color #EB5B08}Processes:${color #EBA713} $processes  ${color #EB5B08}Running:${color #EBA713} $running_processes ${color #EB5B08}

${color #EB5B08}Hard disks:
 ${color #EB5B08}/My system ${color #EBA713}${fs_used /}/${fs_size /} ${fs_bar /}
 ${color #EB5B08}/Home ${color #EBA713}${fs_used /home}/${fs_size /home} ${fs_bar /home}
 ${color #EB5B08}/Elements ${color #EBA713}${fs_used /media/sda2}/${fs_size /media/sda2} ${fs_bar /media/sda2}
${color #EB5B08}/My Book ${color #EBA713}${fs_used /media/sda1}/${fs_size /media/sda1} ${fs_bar /media/sda1}

${color #EB5B08}Wireless Networking:
  ${color #EB5B08}${exec iwconfig wlan0 | grep "ESSID" | cut -c 11-}
  ${color #EB5B08}${exec iwconfig wlan0 | grep "Frequency" | cut -c 25-}
  ${color #EB5B08}Local IP ${color #EBA713}${10.0.0.99} ${color #EB5B08}

  ${color #EB5B08}Download: ${color #EBA713}${totaldown wlan0}	 
  ${color #EB5B08}Upload: ${color #EBA713}${totalup wlan0}

  ${color #EB5B08}Download speed: ${color #EBA713}${downspeed wlan0} k/s${color #EBA713} ${color #EB5B08}   upload speed: ${color #EBA713}${upspeed wlan0} k/s
  ${color #EBA713}${downspeedgraph wlan0 15,150 ff0000 0000ff} $alignr${color #EBA713}${upspeedgraph wlan0) 15,150 0000ff ff0000}


${color #EB5B08}Port(s) / Connections:
${color #EB5B08}Inbound: ${color #EBA713}${tcp_portmon 1 32767 count}  ${color #EB5B08}Outbound: ${color #EBA713}${tcp_portmon 32768 61000 count}  ${color #EB5B08}Total: ${color #EBA713}${tcp_portmon 1 65535 count}
${color #EB5B08}Outbound Connection ${alignr} Remote Service/Port${color #EBA713}
 ${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
 ${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
 ${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
 ${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
 ${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}
```

---

### Post by jryprt on 2008-04-05
I do not know how to help but here is my .conkyrc & it not in is own window
look it over or try it.
```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=9

# Text alpha when using Xft
xftalpha 0.9

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 185 5

# Maximum width
maximum_width 185

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders no

# Stippled borders?
# stippled_borders 8

# border margins
# border_margin 2

# border width
# border_width 1

# Default colors and also border colors
default_color white
default_shade_color red
default_outline_color green

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen


TEXT
${color #88ECE0}SYSTEM ${hr 2}$color
 $nodename   $sysname 
 $kernel  on $machine 
${color #88ECE0}CPU ${hr 2}$color
 Current Speed:   ${freq}MHz   
 Load:${alignr}${loadavg}
 Uptime:${alignr}${uptime}
 ${color}Core 1 Usage:$color ${alignc} ${cpu cpu1}% ${color #EEEEEE}${cpubar cpu1}
 ${color}Core 2 Usage:$color ${alignc} ${cpu cpu2}% ${color #EEEEEE}${cpubar cpu2}
 ${cpugraph 000000 FFFF00}
 CPU                ${alignr}CPU%     MEM%
 ${top name 1}${alignr}${top cpu 1}    ${top mem 1}
 ${top name 2}${alignr}${top cpu 2}    ${top mem 2}
 ${top name 3}${alignr}${top cpu 3}    ${top mem 3}
 
 MEM              ${alignr}CPU%     MEM%
 ${top_mem name 1}${alignr}${top_mem cpu 1}    ${top_mem mem 1}
 ${top_mem name 2}${alignr}${top_mem cpu 2}    ${top_mem mem 2}
 ${top_mem name 3}${alignr}${top_mem cpu 3}    ${top_mem mem 3}

${color #88ECE0}MEMORY / DISK ${hr 2}$color
 RAM:   $mem/$memmax - ${alignr}$memperc%
 ${color #EEEEEE}${membar 6}$color
 ROOT:  ${fs_used /}/${fs_size /}${alignr} -   ${fs_used_perc /}%   
 ${color #EEEEEE}${fs_bar 6 /}$color 
 ${color}DiskI/O:${color}${diskio} 
 ${diskiograph 000000 FFCC33}
${color #88ECE0}WIRED NETWORK: ${hr 2}$color
  ${color #88ECE0}Local IP ${color #c9d6d6}${addr eth0} ${color #c9d6d6}
  ${color #88ECE0}Total Download: ${color #c9d6d6}${totaldown eth01}	 
  ${color #88ECE0}Total Upload: ${color #c9d6d6}${totalup eth0}
  ${color #88ECE0}Download speed: ${color #c9d6d6}${downspeed eth0} k/s${color #c9d6d6} 
  ${color #88ECE0}${downspeedgraph eth0 15,150 ff0000 0000ff} $alignr

  ${color #88ECE0}Upload speed: ${color #c9d6d6}${upspeed eth0} k/s
  ${color #88ECE0}${upspeedgraph eth0 15,150 0000ff ff0000}

${color #88ECE0}Public IP ${color #c9d6d6}${execi 1800 curl 'http://whatismyip.com/automation/n09230945.asp'}

```

---

### Post by kaivalagi on 2008-04-05
Is conky okay if you run it once desktop is fully loaded?

It's just that in Gnome I found that if conky was started on login (via Session settings) it would appear as a window and not flat on the desktop. To solve the issue conky needs to start after the gnome session is complete, a simple sleep command in a script solves that

Hope that helps...

---

