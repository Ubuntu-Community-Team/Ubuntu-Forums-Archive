---
title: "crazy problem with conky. please help..."
date: 2009-06-14
forum: General Help
---

### Post by XxsydenxX on 2009-06-14
My CPU load is always at 100% even though its actually not on the system...this happens with every conky layout i try..this is the one im currently using..any ideas?

background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
$sysname $kernel on $machine

Uptime $alignr $uptime
Load $alignr $loadavg

Hostname $alignr $nodename
eth0 $alignr ${addr eth0}
ppp0 $alignr ${addr ppp0}

Inbound $alignr ${downspeed ppp0} kb/s
${downspeedgraph ppp0}
Outbound $alignr ${upspeed ppp0} kb/s
${upspeedgraph ppp0}

$processes processes ($running_processes running)

CPU $alignr ${cpu cpu0}%
${cpubar cpu0}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}

/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}

swap $alignc $swap / $swapmax $alignr $swapperc%
${swapbar}

---

### Post by Celauran on 2009-06-14
It's not your .conkyrc. I just tried it on my machine and CPU was at 1%.

---

