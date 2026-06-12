---
title: "Conky file for Lenovo Thinkpad T400 or T61"
date: 2014-05-17
forum: Desktop Environments
---

### Post by MepisReign on 2014-05-17
Hello, 
This is a conky configuration file that I modified in order to fit my Thinkpad computers requirements, you need to install hddtemp and conky of course. Anyone with patience could definitely change the colors and tweak it as they wish. 

> 
# .conkyrc - Edited from Russian Conky from Gnome-Look.org
# Edited by Scylla and later for LinuxReign a.k.a. Mepisreign
# Made specifically for the Lenovo T61 and Lenovo T400 with Intel graphics

# --- Window Layout & Options --- #
own_window yes
own_window_colour brown
own_window_transparent yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_spacer right
use_xft yes
alignment top_right
gap_x 10
gap_y 45

# --- Colours, Sizes, Fonts & Margins --- #
update_interval 1.0
maximum_width 250
stippled_borders 3
border_margin 9
border_width 10
default_color grey

# --- Text --- #
draw_outline no
draw_borders no
font Sans:size=8:weight=bold
uppercase no
draw_shades yes
override_utf8_locale yes

TEXT
${font Sans:size=14:weight=bold}${color 7D0101} ${time %r}
${font Sans:size=11:weight=bold}${color grey}${time %A} ${time %e} ${time %B} ${time %G}

${font Sans:size=9:weight=bold}${color 7D0101}SYSTEM INFO${hr 2}$color${font Sans:size=8:weight=bold}
${color 7D0101}Machine$color Thinkpad T400 ${alignr}${color 7D0101} Uptime$color $uptime
${color 7D0101}Kernel$color $kernel ${alignr}${color 7D0101}Type$color $machine

${font Sans:size=9:weight=bold}${color 7D0101}Processor ${hr 2}$color
${font Arial:bold:size=8}${color grey}${execi 99999 cat /proc/cpuinfo | grep "model name" -m1 | cut -d":" -f2 | cut -d" " -f2- | sed 's#Processor ##'}$font$color #004C99
${color 7D0101}Speed:$color ${execi 20 sensors |grep "Core0 Temp" | cut -d" " -f4}$font$color$alignr${freq_g 2}Ghz ${color #c0ff3e}${execi 20 sensors |grep "Core1 Temp" | cut -d" " -f4} $color${alignr}${color 7D0101}Processes:$color $running_processes/ $processes

${font Sans:size=9:weight=bold}${color 7D0101}CPU Usage ${hr 2}$color
${color 7D0101}Core 1 ${color grey}${cpu cpu0}% ${color 7D0101}Core 2 ${color grey}${cpu cpu1}% $color
${cpugraph cpu0 25,120 000000 ff6600 } ${cpugraph cpu1 25,120 000000 ff6600 }
${font Sans:size=8:weight=bold}${color grey}CPU Temp ${color 7D0101}${acpitemp}&#1057;$color
${font Sans:size=8:weight=bold}${color grey}HDD Temp ${color 7D0101} ${execi 10 hddtemp -n /dev/sda} C$color
${font Sans:size=8:weight=bold}${color grey}FAN SPEED ${color 7D0101} ${ibm_fan} rpm$color

${font Sans:size=9:weight=bold}${color 7D0101}TOP 5 CPU Users ${hr 2}$color${font Sans:size=8:weight=bold}${color #ff0000}
Process ${alignr}ID ${alignr}CPU $color
1. ${top name 1} ${alignr}${top pid 1} ${alignr}${top cpu 1}
2. ${top name 2} ${alignr}${top pid 2} ${alignr}${top cpu 2}
3. ${top name 3} ${alignr}${top pid 3} ${alignr}${top cpu 3}
4. ${top name 4} ${alignr}${top pid 4} ${alignr}${top cpu 4}
5. ${top name 5} ${alignr}${top pid 5} ${alignr}${top cpu 5}

${font Sans:size=9:weight=bold}${color 7D0101}TOP 5 RAM Users ${hr 2}$color${font Sans:size=8:weight=bold}${color #ff0000}
Process ${alignr}ID ${alignr}RAM $color
1. ${top_mem name 1} ${alignr}${top_mem pid 1} ${alignr}${top_mem mem 1}
2. ${top_mem name 2} ${alignr}${top_mem pid 2} ${alignr}${top_mem mem 2}
3. ${top_mem name 3} ${alignr}${top_mem pid 3} ${alignr}${top_mem mem 3}
4. ${top_mem name 4} ${alignr}${top_mem pid 4} ${alignr}${top_mem mem 4}
5. ${top_mem name 5} ${alignr}${top_mem pid 5} ${alignr}${top_mem mem 5}

${font Sans:size=9:weight=bold}${color 7D0101}RAM SWAP HDD ${hr 2}$color${font Sans:size=8:weight=bold}
${color 7D0101}RAM$color ${memperc}% ${color grey}${membar 3.180}
${color 7D0101}SWAP$color ${swapperc}% ${color grey}${swapbar 3.180}
${color 7D0101}HDD$color ${fs_used_perc /home}% ${color grey}${fs_bar 3.180 /home}

${font Sans:size=9:weight=bold}${color 7D0101}LAN (IP: ${addr eth0}) ${hr 2}$color${font Sans:size=8:weight=bold}
${color 7D0101}Down$color ${downspeed eth0}&#1050;b/s${alignr}${color 7D0101}Up.$color${alignr} ${upspeed eth0}&#1050;b/s
${downspeedgraph eth0 25,120 000000 00ff00} ${alignr}${upspeedgraph eth0 25,120 000000 ff0000}$color

${font Sans:size=9:weight=bold}${color 7D0101}Wi-fi (IP: ${addr wlan0}) ${hr 2}$color${font Sans:size=8:weight=bold}
${color 7D0101}Down$color ${downspeed wlan0}&#1050;b/s${alignr}${color 7D0101}Up.$color${alignr} ${upspeed wlan0}&#1050;b/s
${downspeedgraph wlan0 25,120 000000 00ff00} ${alignr}${upspeedgraph wlan0 25,120 000000 ff0000}$color


[IMG]http://img.photobucket.com/albums/v297/darth1968/2014-05-17--1400336582_272x713_scrot_zps2aea70d4.png[/IMG]

Best Regards,


MepisReign

---

