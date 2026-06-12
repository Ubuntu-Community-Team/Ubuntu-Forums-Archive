---
title: "conky not behaving"
date: 2009-06-04
forum: Desktop Environments
---

### Post by sn0m on 2009-06-04
Hi guys, I'd appreciate if any of you could have a look at my .conkyrc and tell what I've got wrong.
I have conky on a start up but it stays on top of any other applications/icons rather then in background.
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background no
double_buffer yes
use_spacer yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.5
update_interval 2.0
draw_shades yes
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 4
border_width 1
default_color white
own_window_colour brown
own_window_transparent yes
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 10

TEXT
$color$font
${font LCDMono:size=55}${time %H:%M}$font
${voffset -63}${font Zekton:size=20}${alignr 5}${time %b}$font
${font Zekton:size=20}${alignr 5}${time %y}$font
${color0}${hr 1}$color

${color red}SYSTEM ${hr 1}$color
${color white}${color green}[${color white}$nodename${color green}]:
${color white}$sysname $kernel
${color white}Uptime: $uptime

${color red}CPU ${hr 1}$color
${color green}Load: ${color white}${loadavg} ${color green}
${color green}Processes: ${color white}$processes ${color green}Running: ${color white}$running_processes
${color green}CPU Load: ${color white}${cpu}%
${cpugraph 00ff00 ffffff}
${color green}NAME $alignr PID CPU% MEM%${color white}
${color #ffff00}${top name 1} $alignr ${top pid 1} ${top cpu 1} ${top mem 1}${color white}
${top name 2} $alignr ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4} ${top mem 4}
${top name 5} $alignr ${top pid 5} ${top cpu 5} ${top mem 5}
${top name 6} $alignr ${top pid 6} ${top cpu 6} ${top mem 6}

${color red}MEMORY / DISK ${hr 1}$color
${color green}RAM : ${color white}$memperc% ${color green}(${color white}${mem} / ${memmax}${color green})
${color green}Swap: ${color white}$swapperc% ${color green}(${color white}${swap} / ${swapmax}${color green})
${color green}DiskIO:${color white}${diskio}
${diskiograph 00ff00 ffffff}
${color green}Home: ${color white}${fs_free_perc /home}% ${alignr}${color green}(${color white}${fs_used /home} / ${fs_size /home}${color green})
${color green}sda4: ${color white}${fs_free_perc /media/sda4}% ${alignr}${color green}(${color white}${fs_used /media/sda4} / ${fs_size /media/sda4}${color green})

${color red}NETWORK (${addr wlan0}) ${hr 1}$color
${color green}Down: ${color white}${downspeed wlan0}k/s ${alignr}${color green}Up: ${color white}${upspeed wlan0}k/s
${downspeedgraph wlan0 25,140 ff0000 00ff00} ${alignr}${upspeedgraph wlan0
25,140 00ff00 ff0000}
${color green}Total: ${color white}${totaldown wlan0} ${alignr}${color green}Total: ${color white}${totalup wlan0}
${color green}Inbound: ${color white}${tcp_portmon 1 32767 count} ${color green}Outbound: ${color white}${tcp_portmon 32768
61000 count}${alignr}${color green}Total: ${color white}${tcp_portmon 1 65535 count}
${color green}Connections ${color white}${tcp_portmon 32768 61000 count}
Connections ${tcp_portmon 32768 61000 count} ${alignr} Service/Port
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}

${color red}Temps ${hr 1}$color
${color green}CPU1 Temp: ${color white}${execi 10 sensors | grep -A0 'Core 0' | cut -c15-16} C
${color green}CPU2 Temp: ${color white}${execi 10 sensors | grep -A0 'Core 1' | cut -c15-16} C
${color green}Motherboard Temp: ${color white}${execi 10 sensors | grep -A0 'temp1' | cut -c15-16} C
${color green}SDA2 Temp: ${color white}${execi 10 hddtemp /dev/sda2 | grep -A0 'SAMSUNG HM121HI' | cut -c28-35} 
${color green}Battery: ${color white}${execi 10 acpi | grep -A0 'Battery 0' | cut -c15-60}
 and this is a picture of my desktop

---

### Post by sn0m on 2009-06-04
Hi guys, i sorted it by writing a little script to delay its start.
This is it if anyone's interested:
#!/bin/sh
#script to run conky
sleep 20s &&
/usr/bin/conky
#this is it
you then can go to Preferences>start up applications and add it on.
regards
Sokol

---

