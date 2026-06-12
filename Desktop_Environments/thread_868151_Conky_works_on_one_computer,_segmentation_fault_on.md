---
title: "Conky works on one computer, segmentation fault on the other"
date: 2008-07-23
forum: Desktop Environments
---

### Post by altonbr on 2008-07-23
I've installed Conky 1.5.1 in Hardy through apt-get and it seems it has trouble displaying conky on my Xubuntu laptop as opposed to my Ubuntu desktop and server.

The Xubuntu laptop seems to be able to use the default conky theme, but not my custom one that works on the other two machines mentioned above, both using Hardy as well.

Here is the /etc/conky/conky.conf that works with Xubuntu:
```
alignment bottom_left
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_class Conky
own_window_type normal
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer none

TEXT
$nodename - $sysname $kernel on $machine
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 / $color${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} k/s${color grey} - Down:$color ${downspeed eth0} k/s
$hr
${color grey}Name                  PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

```

Here is my .conkyrc file that throws a segmentation fault on the Xubuntu laptop:
```
# Inspired by:
# http://ubuntuforums.org/showpost.php?p=1880108&postcount=40

# window
own_window yes
own_window_hints undecorated,below,skip_taskbar
own_window_colour brown
own_window_transparent yes
background yes

# aethetics
draw_shades no
draw_outline no
draw_borders no
use_spacer none

# fonts
use_xft yes
xftfont Trebuchet MS:size=8
uppercase no
default_color white

# update
double_buffer yes
update_interval 3

# size
minimum_size 400 5
maximum_width 200

# borders
stippled_borders 3
border_margin 9
border_width 10

# alignment
alignment top_right
gap_x 10
gap_y 20

TEXT
${alignc}${exec whoami} @ ${nodename}
${alignc}${uptime}

${alignc}mobile AMD Athlon 4 @ ${freq}MHz
${cpugraph cpu0 25,95}${alignr}${cpugraph cpu1 25,95}

${alignc}${running_processes}/${processes}
${top name 1} ${alignr}${top cpu 1}
${top name 2} ${alignr}${top cpu 2}
${top name 3} ${alignr}${top cpu 3}

mem ${alignr}${membar 5,150}${color}
swap ${alignr}${swapbar 5,150}${color}

${top_mem name 1} ${alignr}${top_mem mem 1}
${top_mem name 2} ${alignr}${top_mem mem 2}
${top_mem name 3} ${alignr}${top_mem mem 3}

/ ${alignr}${fs_bar 5,150 /}${color}
${diskiograph}

${alignc}${addr eth0}
${alignc}${tcp_portmon 1 65535 count} connections${alignr}
${downspeed eth0} kB/s ${alignr}${upspeed eth0} kB/s
${downspeedgraph eth0 25,95} ${alignr}${upspeedgraph eth0 25,95}

${tcp_portmon 32768 61000 rhost 0}${alignr}${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1}${alignr}${tcp_portmon 32768 61000 rservice 1}


```

Is it possible that Xubuntu has some libraries missing? The only major difference between the laptop and the desktop/server is that the laptop is AMD and the desktop and server are Intel-based. I don't think it should matter though.

---

