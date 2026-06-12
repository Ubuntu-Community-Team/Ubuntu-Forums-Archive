---
title: "conky doesn't display cpu temp on 64bit"
date: 2010-02-03
forum: Desktop Environments
---

### Post by pistacoppu on 2010-02-03
Hi,
I found that a couple of people posted the same problem on the huge thread about .conkyrc file, but they received no answer.
The problem is that: i switched from ubuntu 9.10 32 to 64 bit, and if i use the same .conkyrc that i used to:

```

alignment top_right
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
use_xft yes
xftfont DejaVu Sans Mono:size=9
gap_x 5
gap_y 5
minimum_size 5 5
net_avg_samples 2
#no_buffers no
double_buffer yes
out_to_console no
out_to_stderr no
extra_newline no

own_window yes

#own_window_class Conky
own_window_type override
own_window_transparent yes

stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

TEXT
$nodename - $sysname $kernel on $machine 
${color grey}Uptime:$color $uptime
${color #B8FF00}SISTEMA ${hr 2}
#	CPU
#${color grey}Frequency (in MHz):$color $freq
#${color grey}Frequency (in GHz):$color $freq_g
#${color #d0002a}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'}
#${color #d0002a}CPU Temperature: ${alignr}${color white}${acpitemp} C
${color grey}Core 1:${color white} ${freq_g 1}Ghz  ${color grey}Temp: ${color white}${execi 8 sensors | grep -A 1 'Core 0' | cut -c13-16 | sed '/^$/d'} °C 
${color grey}Core 2:${color white} ${freq_g 2}Ghz  ${color grey}Temp: ${color white}${execi 8 sensors | grep -A 1 'Core 1' | cut -c13-16 | sed '/^$/d'} °C 
${color grey}GPU:${color white}${nvidia gpufreq}Mhz ${color grey}Temp: ${color white}${nvidia temp} °C
#	SISTEMA
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${color f6ff07}${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${color f6ff07}${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${color f6ff07}${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
${color #B8FF00}DISCHI ${hr 2}
${color grey}File systems:
 / $color${fs_used /}/${fs_size /} ${color f6ff07}${fs_bar 4 /}
${color grey}Data:
 / $color${fs_used /media/DATA}/${fs_size /media/DATA} ${color f6ff07}${fs_bar 4 /media/DATA}
#	RETE
${color #B8FF00}INTERNET ${hr 2}
${color #B8FF00}WiFi:${color white} ${wireless_essid wlan0} ${color grey}Up:$color ${upspeed wlan0} ${color grey} - Down:$color ${downspeed wlan0}
${color #B8FF00}Wind 3G:  ${color grey}Up:$color ${upspeed ppp0} ${color grey} - Down:$color ${downspeed ppp0}
#${color grey}Public IP: ${color white}(${execi 3600 wget -O - http://whatismyip.org/ | tail})
# 	GMAIL
${color #B8FF00}Gmail ${hr 2}
${color}You have ${color #B8FF00}${texeci 100 python ~/.scripts/gmail.py} ${color}new gmail(s).
${execi 60 python ~/.scripts/gmail.py s}
${color #B8FF00}PROCESSI ${hr 2}
${color grey}Name              PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
#	CALENDAR
${color #B8FF00}DATE ${hr 2}
${alignc 45}${font Trebuchet MS:size=12}${time %a %d %b %Y}    -    ${time %H:%M}${font}
${color white}${font DejaVu Sans Mono:size=10}${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color f6ff07}'"$DJS"'${color white}'" "/}${color white}${font}

```

cpu temp is not displayed.
I've installed lmsensors, did sensors-detect and installed the missing package called coretemp , for my intel processor.
Why that .conkyrc worked on 32bit?
thanks

p.s. frequency information is working fine

---

### Post by proxess on 2010-02-03
Try sensors-detect again, plus install sensord, and reboot.

EDIT: Are you sure coretemp is really necessary? What CPU do you have?

---

### Post by pistacoppu on 2010-02-03
hi, i need cpu temp because i do a lot of CFD and sometime my laptop gets really hot, i have a centrino duo t9400.
By the way, i just needed a reboot, after installing coretemp.
I mark thread as solved.
Ciao.

---

