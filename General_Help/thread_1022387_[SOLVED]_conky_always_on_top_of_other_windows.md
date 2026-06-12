---
title: "[SOLVED] conky always on top of other windows"
date: 2008-12-26
forum: General Help
---

### Post by oddworld on 2008-12-26
Conky is always on top of other windows.
What is wrong?

```

background yes
font Zekton:size=14
xftfont Zekton:size=14
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
on_bottom yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 220 5
maximum_width 220
default_color d7d7d7
default_shade_color black
default_outline_color black
alignment top_right
gap_x 20
gap_y 60
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
${font Zekton:style=Bold:pixelsize=42}${alignc}${time %H:%M}${font Zekton:size=11}
Hostname: $alignr$nodename
Kernel: $alignr$kernel 
Uptime: $alignr$uptime 
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg
CPU       ${alignc} ${freq 1}MHz X2 ${alignr}(${cpu cpu0}%)
${cpubar 4 cpu0}
${cpugraph}
Core 1 ${cpu cpu1}% $alignr Core 2 ${cpu cpu2}%
${cpugraph cpu1 25,90 } $alignr${cpugraph cpu2 25,90 }
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}
Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1} ${top mem 1}
${top name 2}$alignr${top cpu 2} ${top mem 2}
${top name 3}$alignr${top cpu 3} ${top mem 3}
${top name 4}$alignr${top cpu 4} ${top mem 4}
${top name 5}$alignr${top cpu 5} ${top mem 5}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1} ${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2} ${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3} ${top_mem mem 3}
${top_mem name 4}$alignr${top_mem cpu 4} ${top_mem mem 4}
${top_mem name 5}$alignr${top_mem cpu 5} ${top_mem mem 5}
Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}

Down ${downspeed wlan0} k/s ${alignr}Up ${upspeed wlan0} k/s
${downspeedgraph wlan0 55,107} ${alignr}${upspeedgraph wlan0 55,107}
Total ${totaldown wlan0} ${alignr}Total ${totalup wlan0}

```

---

### Post by MarblePanther on 2008-12-26
You can try:

background yes

own_window_type normal
OR:
own_window_type desktop

---

### Post by oddworld on 2008-12-26
Thanks, the solution was

own_window_type desktop

---

### Post by MarblePanther on 2008-12-26
glad to help

---

### Post by hittudiv on 2010-08-13
i want the reverse..
I want conky to stay on top.
and i dont want it to disturb the work
can it be made transparent and click-through?

---

### Post by ssuuddoo on 2010-12-19
click-through would be great

---

