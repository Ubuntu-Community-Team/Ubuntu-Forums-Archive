---
title: "Odd conky config conflict?"
date: 2010-04-12
forum: Desktop Environments
---

### Post by iTrascurato on 2010-04-12
So, I am having a very odd issue with my conky / conky configuration.

It works.. as it has been.  Then, wouldn't load up upon startup.. or manually.

Loading my back up config makes it work fine, but changing it a little bit will cause it not to work.  Now, here is the real issue.  Down the bottom, the ~/.wan-ip script is now not hidden on my filesystem.  Conky will load but obviously without that wan-ip field displaying any information.  Fine.

This is what I don't understand.  In this config file, changing from .**wan-ip** to **wan-ip** will make conky not load visually.  So I change it back.. and it loads.  Now.. changing the actual NAME of the file on my filesystem for that script TO **.wan-ip** to just be compatible with my old script will also make conky not load at all.

This is very odd.  Config is below.  I've also tried defining ~/.wan-ip as /home/brendan/wan-ip   (with or without the dot).  No difference.

```
background no
use_xft yes
xftfont Terminus:size=7
xftalpha 0.8
update_interval 2.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undercorated.below.skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
draw_shades yes
draw_outline no
draw_borders no
stippled_borders 8
border_margin 4
border_width 1
default_color white
default_shade_color black
default_outline_color white
alignment top_right
gap_x 10		
gap_y 18
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
use_spacer right


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %Y}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}${cpugraph cpu0 42AE4A eeeeee}
${offset 240}${color slate grey}Core 1 $alignr Core 2
${offset 240}${color slate grey}${cpugraph cpu1 15,60 42AE4A eeeeee} $alignr${cpugraph cpu2 16,60 42AE4A eeeeee}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc%
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc%
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_used /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_used /home/brendan}/${fs_size /home/brendan}
${offset 240}${fs_bar 3,100 /home}

${offset 240}${color slate grey}NET:
${offset 240}${color}LAN: ${color }$alignr${addr eth0}
${offset 240}${color}WAN: ${color }$alignr${execi 600 ~/.wan-ip}
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}


```

---

### Post by iTrascurato on 2010-04-12
Update:  It now works, without any changes.

Has anybody experienced this kind of inconsistency with conky?

---

