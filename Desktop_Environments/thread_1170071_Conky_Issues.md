---
title: "Conky Issues"
date: 2009-05-25
forum: Desktop Environments
---

### Post by setsanto on 2009-05-25
Hi,

I've been using conky fairly successfully for a while now.  Recently I installed WinXP through Virtualbox, and ever since then I've been getting the same problem (I have no idea if it's related).  Whenever I try and start conky, nothing happens.  When I try open it through terminal, I get this:

```
nick@nick-desktop:~$ conky
Conky: forked to background, pid is 10240
nick@nick-desktop:~$ 
Conky: desktop window (100007c) is subwindow of root window (52)
Conky: window type - override
Conky: drawing to created window (0x4200001)
Conky: drawing to double buffer
Conky: attempting to use more CPUs than you have!
obj->data.cpu_index 2 info.cpu_count 1

```

Any ideas?  If you need me conky config file, it's this:

```
use_xft yes
xftfont Arial:bold:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 5
border_margin 0
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 79D700
color2 AAAAAA
color3 FFFFFF
background yes



TEXT
${font Arial:bold:size=10}${font Arial:bold:size=10}${color1}TIME ${color2}${hr 2}

${color3} ${voffset -20}${font :size=30}$alignc${time %H:%M}
${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
${font :bold:size=8}$alignc${time %A}

${color1}WEATHER ${color2}${hr 2}
${font}${color3}${font Weather:size=45}${execi 1800 conkyForecast --location=CAXX0333 --datatype=WF}
${voffset -50}${font Arial:bold:size=10}${color3}${execi 1800 conkyForecast --location=CAXX0333 --datatype=LT} / ${execi 1800 conkyForecast --location=CAXX0333 --datatype=HT}
$font${voffset -55}${alignr}${color3}Wind: ${execi 1800 conkyForecast --location=CAXX0333 --datatype=WS}
${alignr}${color3}Humidity: ${execi 1800 conkyForecast --location=CAXX0333 --datatype=HM}
${alignr}${color3}${execi 1800 conkyForecast --location=CAXX0333 --datatype=CT}

${color3}Sunrise$alignr${execi 1800 conkyForecast --location=CAXX0333 --datatype=SR}${alignr}
Sunset$alignr${execi 1800 conkyForecast --location=CAXX0333 --datatype=SS}$color

${font Arial:bold:size=10}${color1}SYSTEM ${color2} ${hr 2}
$font${color3}$sysname $kernel $alignr $machine
Intel Pentium D $alignr${freq_g cpu0}Ghz
Uptime $alignr${uptime_short}
File System $alignr${fs_type}

${font Arial:bold:size=10}${color1}PROCESSORS ${color2}${hr 2}
$font${color3}CPU1$alignr${cpu cpu1}%
${cpubar cpu1}
CPU2$alignr${cpu cpu2}%
${cpubar cpu2}

${font Arial:bold:size=10}${color1}MEMORY/HDD ${color2}${hr 2}
$font${color3}RAM $alignc $mem / $memmax $alignr $memperc%
$membar
${voffset -1}$font${color3}/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
/windows $alignc ${fs_used /media/windows} / ${fs_size /media/windows} $alignr ${fs_free_perc /media/windows}%
${fs_bar /media/windows}

${font Arial:bold:size=10}${color1}NETWORK ${color2}${hr 2}
$font${color3}Internal IP$alignr${addr eth0}

Downloaded$alignr  ${totaldown eth0}
Uploaded$alignr  ${totalup eth0}

Down Speed$alignr  ${downspeed eth0}kb/s
Up Speed$alignr  ${upspeed eth0}kb/s

${font Arial:bold:size=10}${color1}TOP PROCESSES ${color2}${hr 2}
${color3}$font${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %

${voffset -10}${font Arial:bold:size=10}${color1}TODO ${color2}${hr 2}
$font${color3}${execi 30 cat /home/nick/TODO.txt | fold -w40 }

${font Arial:bold:size=10}${color1}FOLDING@HOME ${color2}${hr 2}
$font${color3}${exec ~/scripts/.fah_status.sh}
```

~Setsanto

---

### Post by iiska on 2009-05-26
You are trying to graph data from three different CPU's in your .conkyrc. Remove lines which refer to cpu1 and cpu2, and then it should work.

---

