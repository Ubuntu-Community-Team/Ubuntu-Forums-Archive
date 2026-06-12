---
title: "Minor issues with my conky (karmic 9.10)"
date: 2010-02-03
forum: Desktop Environments
---

### Post by 786souljah on 2010-02-03
Here's a small problem I've noticed and wondered if anyone can help me out. I've posted the conky config I've got running below.

```

minimum_size 290 6
maximum_width 290
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 10
gap_y 10
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer right

TEXT



${alignc}${color #d0002a}The h4ckt0p

${alignc}${color #d0002a}${time %I:%M:%S}
${alignc}${color #d0002a}${time %a. %b. %d, %G}


${color #d0002a}$sysname $kernel $machine ${alignr}$nodename 

${color #d0002a}Uptime:${color lightgrey} $uptime ${color #d0002a} ${alignr}Load:${color lightgrey} $loadavg

${color #d0002a}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'}

${color #d0002a}CPU Temperature: ${alignr}${color white}${acpitemp} C

${color #d0002a}CPU Usage:${color #d0002a} ${color lightgrey}${cpu}% ${color #d0002a}${cpubar}
${color #d0002a}${cpugraph 000000 ff0900}

${color #d0002a}CPU Usage  ${alignr}PID   CPU%   MEM%
${color   white}  ${top name 1} ${alignr}${top pid 1} ${top cpu 1} ${top mem 1}
${color #d0002a}  ${top name 2} ${alignr}${top pid 2} ${top cpu 2} ${top mem 2}
${color #d0002a}  ${top name 3} ${alignr}${top pid 3} ${top cpu 3} ${top mem 3}

${color #d0002a}Memory Usage
${color   white}  ${top_mem name 1} ${alignr}${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #d0002a}  ${top_mem name 2} ${alignr}${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #d0002a}  ${top_mem name 3} ${alignr}${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color #d0002a}RAM:${color lightgrey} $mem/$memmax - $memperc% ${alignr}${color #d0002a}${membar 5,110}
${color #d0002a}SWAP:${color lightgrey} $swap/$swapmax - $swapperc% ${alignr}${color #d0002a}${swapbar 5,110}

${color #d0002a}Hard Disks:
${color #d0002a} Root: ${color lightgrey}${fs_used /}/${fs_size /}${alignr}${color #d0002a}${fs_bar 5,120 /}
${color #d0002a} Home: ${color lightgrey}${fs_used /home}/${fs_size /home}${alignr}${color #d0002a}${fs_bar 5,120 /home}


${color #d0002a}Hard Drive I/O: ${alignr}${color lightgrey}${diskio}
${color #d0002a}${diskiograph 000000 ff0900 -l}

${color #d0002a}Battery Status: ${alignr}${color white}${battery_percent} % Charge Left

```

The issue I have is an annoying one, though minor. When conky displays, I notice it flashes once every 3 to 5 seconds, then reappears; or even completely disappears and then reappears a few seconds later.

Any ideas as to what may be causing this? 

Thanks for any help.

---

### Post by Orlando84 on 2010-02-03
Try to modify /etc/X11/xorg.conf, find section "Module" and add string
Load "dbe"

Then modify your ~/.conkyrc :
double_buffer yes
own_window yes
own_window_type normal
own_window_hints below,sticky,undecorated,skip_taskbar

---

### Post by 786souljah on 2010-02-04
I don't know what solved my problem but I used a new script and modified it to my liking and seems to have resolved the problems I was having previously. 

I did notice the script included that line you suggested I add. That may have been it. Thanks for the help.

---

