---
title: "Conky starts with large font"
date: 2009-02-26
forum: Desktop Environments
---

### Post by hisotaso on 2009-02-26
When conky starts up automatically, it has a font of about oh i dunno size 14? Anyway in my .conkyrc i have it set to 9, and when I run conky through terminal, it starts in large font also, but once i close terminal it goes down to size 9. Any idea why this is happening?

Heres my .conkyrc:

background no
xftfont URW Bookman L Light:size=9
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color green
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase

TEXT
${color red}SYSTEM ${hr 1}${color}

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Temp: ${alignr}${acpitemp}C

CPU: ${alignr}${freq} MHz
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

${color red}MEMORY / CPU${hr 2}$color

CPU1 ${alignr}${cpu cpu1}%
${cpubar 4 cpu1}
CPU2 ${alignr}${cpu cpu2}%
${cpubar 4 cpu2}

Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}
swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${color red}Filesystem ${hr 1}${color}

Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /home}
Windows (C:): ${alignr}${fs_free /media/c} / ${fs_size /media/c}
${fs_bar 4 /media/c}
Storage (E:): ${alignr}${fs_free /media/E} / ${fs_size /media/E}
${fs_bar 4 /media/E}
Heather (D:): ${alignr}${fs_free /media/heather} / ${fs_size /media/heather}
${fs_bar 4 /media/heather}

${color red}NETWORK ${hr 1}${color}

Public IP:$alignr${execi 600 /home/jeremiah/Scripts/.wan-ip}
Local Ip: ${alignr}${addr eth0}
Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107} ${alignr}${upspeedgraph eth0 25,107}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

${color red}WEATHER ${hr 1}${color}

${execi 1800 /home/jeremiah/Scripts/weather.sh SWXX0006}

---

### Post by hisotaso on 2009-03-01
bump

---

