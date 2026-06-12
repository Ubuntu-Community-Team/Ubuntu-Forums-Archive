---
title: "Need help with my conky config"
date: 2009-02-01
forum: General Help
---

### Post by wikid_one on 2009-02-01
I have been working on updating my conky config.  I have everythign finished, except for one little problem I cannot figure out.

```
background no
font Bitstream Vera Sans:size=7
xftfont Bitstream Vera Sans:size=7
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 900 100
maximum_width 900
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color black
alignment top_middle
gap_x 0
gap_y 0
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase yes

TEXT
${font Bitstream Vera Sans:size=10}Info${font}
Kernel: $kernel
Uptime: $uptime

Processes: $processes ($running_processes running)
Load: $loadavg

Battery Life: ${battery_percent BAT0}%

${voffset -112}${offset 160}${font Bitstream Vera Sans:size=10}System${font}
${offset 160}CPU1: ${freq_g 1} GHz ${alignr}${offset -580}${cpu cpu1}%
${offset 160}CPU2: ${freq_g 2} GHz ${alignr}${offset -580}${cpu cpu2}%
${offset 160}${cpubar 4,160 cpu1}
${offset 160}Ram: ${alignr}${offset -580}$mem / $memmax ($memperc%)
${offset 160}${membar 4,160}
${offset 160}swap: ${alignr}${offset -580}$swap / $swapmax ($swapperc%)
${offset 160}${swapbar 4,160}

${offset 160}Processes${alignr}${offset -580}CPU   Mem
${offset 160}${top name 1}${alignr}${offset -580}${top cpu 1} ${top mem 1}
${offset 160}${top name 2}${alignr}${offset -580}${top cpu 2} ${top mem 2}
${offset 160}${top name 3}${alignr}${offset -580}${top cpu 3} ${top mem 3}
${offset 160}${top name 4}${alignr}${offset -580}${top cpu 4} ${top mem 4}
${offset 160}${top name 5}${alignr}${offset -580}${top cpu 5} ${top mem 5}

${voffset -195}${offset 345}${font Bitstream Vera Sans:size=10}Filesystem${font}
${offset 345}/: ${alignr}${offset -395}${fs_used /} / ${fs_size /}
${offset 345}${fs_bar 4,160 /}
${offset 345}/Boot: ${alignr}${offset -395}${fs_used /boot} / ${fs_size /boot}
${offset 345}${fs_bar 4,160 /boot}
${offset 345}/Home: ${alignr}${offset -395}${fs_used /home} / ${fs_size /home}
${offset 345}${fs_bar 4,160 /home}

${voffset -102}${offset 525}${font Bitstream Vera Sans:size=10}Network${font}
${offset 525}Internal IP: ${addr eth0}
${offset 525}External IP: ${execi 3600 wget -O - http://whatismyip.org/ | tail}

${offset 525}Down: ${downspeed eth0} k/s
${offset 525}${downspeedgraph eth0 15,140}
${offset 525}Up: ${upspeed eth0} k/s
${offset 525}${upspeedgraph eth0 15,140}

${voffset -136}${offset 680}${font Bitstream Vera Sans:size=10}Notes${font}
${offset 680}${exec cat ~/.conky/notes}
```

The area I am focusing on is the last section (Notes).  I am just reading a text file that I use as a reminder for homework/events.  I want the whole section to be aligned under the notes header, but the offset command is only passed to the first line in the text file.  How do I modify my config so it gets passed to all items in the text file?

The attached screenshot shows my problem.  The first line is in the correct spot, but the next 2 lines are left allgned.

Thanks.

---

### Post by easybake on 2009-02-02
I've come across this problem before but haven't yet found an easy fix.

The best thing would be to probably use a separate conky just to handle that section. 

Just use the conky -c command to launch the second one.
e.g ```
conky -c /home/easybake/todolist
```

---

