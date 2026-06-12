---
title: "Conky Problem"
date: 2009-07-11
forum: Desktop Environments
---

### Post by MZaza on 2009-07-11
Hello

I'm trying to edit the .conkyrc to not show borders, here's how the conky looks on my desktop to understand better [IMG]http://img23.imageshack.us/img23/3084/screenshot1imv.png[/IMG]

 and here's my configuration

```
# Conkyrc by Hund @ ebupof.deviantart.com
# Sry for the chaos below, but atleast it works! ;)


use_xft yes
xftfont DejaVu Sans:size=6
xftalpha 0.8
text_buffer_size 2048
draw_shades no
draw_outline no
draw_borders no
background no
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints below,undecorated
double_buffer yes
minimum_size 220 5
maximum_width 300
draw_graph_borders yes
default_color black
default_shade_color black
alignment top_right
gap_x 12
gap_y 28
cpu_avg_samples 2
override_utf8_locale no
uppercase yes

TEXT

Kernel: $alignr $kernel
Uptime: $alignr $uptime

$stippled_hr
SYSTEM
$stippled_hr

CPU1: ${alignr} ${cpu cpu1}%
CPU2: ${alignr} ${cpu cpu2}%
${cpugraph 20}
Load: $alignr $loadavg
Processes: $alignr $processes
Running: $alignr $running_processes

RAM: $alignr $mem/$memmax
${membar 3}
Swap: $alignr $swap / $swapmax
${swapbar 3}

$stippled_hr
TOP
$stippled_hr

Name $alignr PID     CPU%   MEM%
${color #ddaa00} ${top name 1} $alignr ${top pid 1} ${top cpu 1} ${top mem 1}$color
 ${top name 2} $alignr ${top pid 2} ${top cpu 2} ${top mem 2}
 ${top name 3} $alignr ${top pid 3} ${top cpu 3} ${top mem 3}

Mem usage$color
${color #ddaa00} ${top_mem name 1} $alignr ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}$color
 ${top_mem name 2} $alignr ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
 ${top_mem name 3} $alignr ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

$stippled_hr
HDD
$stippled_hr

I/O:

 Write: $alignr $diskio_write
${diskiograph_write 20}
 Read: $alignr $diskio_read
${diskiograph_read 20}

ROOT: $alignr ${fs_free /} / ${fs_size /}
${fs_bar 3 /}
HOME: $alignr ${fs_free /home} / ${fs_size /home}
${fs_bar 3 /home}

$stippled_hr
Network
$stippled_hr

Down:
${color #ddaa00} Speed: $alignr ${downspeed eth0} k/s$color
 Tot: $alignr ${totaldown eth0}

${downspeedgraph eth0 20} ${alignr}${upspeedgraph eth0 20}

Up:
${color #ddaa00} Speed: $alignr ${upspeed eth0} k/s$color
 Tot: $alignr ${totalup eth0}

${upspeedgraph eth0 20} ${alignr}${upspeedgraph eth0 20}

```

---

### Post by VCoolio on 2009-07-11
It's not borders, it's dropshadow. If you use compiz gp to window decoration plugin and in entry field for shadow windows add:
```
!(class=Conky)
```
or maybe conky, I keep forgetting if it needs the capital or not. The exclamation mark means to indicate an exception to the rule of drawing dropshadows.

---

### Post by MZaza on 2009-07-11
> **VCoolio said:**
> It's not borders, it's dropshadow. If you use compiz gp to window decoration plugin and in entry field for shadow windows add:
```
!(class=Conky)
```
or maybe conky, I keep forgetting if it needs the capital or not. The exclamation mark means to indicate an exception to the rule of drawing dropshadows.

From where can I edit the compiz decoration plugin?

---

### Post by VCoolio on 2009-07-11
Only if you use compiz, in system > preferences > compiz config settings manager. If that isn't there, install package compizconfig-settings-manager. Then open it, click the button for window decorations and follow instructions from previous post.

---

### Post by ~sHyLoCk~ on 2009-07-11
> **MZaza said:**
> From where can I edit the compiz decoration plugin?

Try:```

own_window_type desktop
```

---

