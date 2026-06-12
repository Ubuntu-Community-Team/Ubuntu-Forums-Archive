---
title: "Conky Disappears, then Reappears"
date: 2007-08-04
forum: Desktop Effects &amp; Customization
---

### Post by thexaspect on 2007-08-04
Hey there, I'm having a problem getting conky to stick around. It shows up for about a second, then disappears, and as soon as I restart or shutdown, it pops back up for a couple of seconds, and then obviously disappears again. Anyone have any ideas? I'm including my .conkyrc

```
background yes
xftfont FreeSans:size=9
use_xft yes
xftalpha 0.9
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
SYSTEM ${hr 1}

Hostname $alignr$nodename
Kernel $alignr$kernel
Uptime $alignr$uptime
Processes ${alignr}$processes ($running_processes running)

CPU1 ${alignr}${cpu cpu1}%
${cpubar cpu1}
MEM ${alignr}$mem of $memmax ($memperc%)
$membar
swap ${alignr}$swap of $swapmax ($swapperc%)
$swapbar

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

DISK USAGE ${hr 1}

/ ${alignr}${fs_used /} of ${fs_size /} (${fs_used_perc /}%)
${fs_bar /}
/home ${alignr}${fs_used /home} of ${fs_size /home} (${fs_used_perc /home}%)
${fs_bar /home}

NETWORK ${hr 1}

IP Address  $alignr${addr eth1}
Signal Strength $alignr${linkstatus eth1}%
Down ${downspeed eth1} k/s ${alignr}Up ${upspeed eth1} k/s
${downspeedgraph eth1 25,107} ${alignr}${upspeedgraph eth1 25,107}
Total ${totaldown eth1} ${alignr}Total ${totalup eth1}
Inbound ${tcp_portmon 1 32767 count} ${alignr}Outbound ${tcp_portmon 32768 61000 count}

WEATHER ${hr 1}

${execi 1800 /home/x/.conkyweather.sh CHXX0008}
```

Thanks for taking a look =)

---

### Post by psyopper on 2007-08-04
Remove the line:

own_window_type override

Or you can change the value to desktop which is the default you would get by removing the line...

Let us know how it works!

---

### Post by thexaspect on 2007-08-05
Thank you my friend you are amazing! I guess that's what I get for copying and pasting from a friends..... =)

---

