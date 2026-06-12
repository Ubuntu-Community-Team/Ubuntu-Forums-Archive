---
title: "Can someone give me a hand on getting Rhythm Box working in Conky?"
date: 2010-03-07
forum: Desktop Environments
---

### Post by RiseAgainst540 on 2010-03-07
Here's my Conky config file. 

```
background yes
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 400
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color gray
default_shade_color red
default_outline_color green
alignment top_right
gap_x 10
gap_y 10
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer yes
text_buffer_size 256

TEXT


${font openlogos:size=20}U${font Arial:size=20}${color Tan1}Ubuntu${color Ivory}LINUX${font openlogos:size=20}t

${voffset -90}
${color DimGray}
${font}
${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
$font${color DimGray}$sysname $kernel $alignr $machine
AMD Phenom™ X4 $alignr${freq_g cpu0}Ghz
Uptime $alignr${uptime}
File System $alignr${fs_type}

${font Arial:bold:size=10}${color Tan1}PROCESSORS ${color DarkSlateGray}${hr 2}
$font${color DimGray}CPU1  ${cpu cpu1}% ${cpubar cpu1}
CPU2  ${cpu cpu2}% ${cpubar cpu2}

${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
$font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
$membar

${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
$font${color DimGray}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
$font${color DimGray}/media/MY BOOK $alignc ${fs_used /media/MY BOOK} / ${fs_size /media/MY BOOK} $alignr ${fs_free_perc /media/MY BOOK}%
${fs_bar /media/MY BOOK}


${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %


${font Arial:bold:size=10}${color Tan2}TIME ${color DarkSlateGray}${hr 2}

${color DarkSlateGray} ${font :size=30}$alignc${time %H:%Mh}
${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
${font :bold:size=8}$alignc${time %A}
```


Need help getting rhythmbox working.

---

### Post by stinkeye on 2010-03-07
[**_[COLOR="DarkRed"]Conky Rhythmbox Python Script[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=928168")

---

