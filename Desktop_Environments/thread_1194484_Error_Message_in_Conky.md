---
title: "Error Message in Conky"
date: 2009-06-22
forum: Desktop Environments
---

### Post by NoctisCaelum on 2009-06-22
I've putted this config in my conky:

```
# 9ooo1_simple_conkyrc_v0.2

# --- Window Layout & Options --- #
own_window yes
own_window_colour brown
own_window_transparent yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_spacer right
use_xft yes
alignment top_right
gap_x 10
gap_y 30

# --- Colours, Sizes, Fonts & Margins --- #
update_interval 1.0
maximum_width 260
stippled_borders 3
border_margin 9
border_width 10
default_color B1B1B1

# --- Text --- #
draw_outline no
draw_borders no
font Arial:size=9:weight=bold
uppercase no
draw_shades yes

TEXT

${alignc}${time %A},${time %e} de ${time %B} de ${time %G}

${alignc}${time %H:%M:%S}

$nodename ${alignr} Tempo ligado: $uptime

Sistema: $kernel em uma máquina $machine

${alignc}${execi 99999 cat /proc/cpuinfo | grep "model name" -m1 | cut -d":" -f2 | cut -d" " -f2- | sed 's#Processor ##'}
Frequência: ${freq_g 2}GHz ${alignr}
Uso do processador: ${cpu cpu1}%
Processos: $running_processes/$processes
${cpugraph cpu1 25,260 000000 93C9EB}
${cpubar cpu1 10,260 000000 93C9EB}

Temperatura do processador: ${hwmon 0 temp 2}°C
Temperatura do sistema: ${hwmon 0 temp 1}°C


Memória RAM ${membar 5}
Usada: $mem $alignr Total: $memmax

Partição Swap ${swapbar 5}
Usada: $swap $alignr Total: $swapmax



Disco do Linux ${fs_bar 5 /}
Livre: ${fs_free /} $alignr Usado: ${fs_used /}

Disco do Windows ${fs_bar 5 /media/disk}
Livre: ${fs_free /media/disk} $alignr Usado: ${fs_used /media/disk}



$alignc ppp0 (${addr ppp0})
Download: ${downspeed ppp0} KB/s${alignr} Upload: ${upspeed ppp0} KB/s
${downspeedgraph ppp0 25,120 000000 93C9EB} ${alignr}${upspeedgraph ppp0 25,120 000000 93C9EB}$color
Total: ${totaldown ppp0} ${alignr}Total: ${totalup ppp0}
```this config wasn't made by me. When I try to load conky the next message appear to me: 
"Conky can't open '/sys/class/hwmon/hwmon0/device/temp2_input' : No such file or directory"
"Please check your device or remove this var from conky"

I tried to edit some part of the code but I couldn't get ride of this error.

Anyone can help me ?

[COLOR=Red]**EDIT:**[/COLOR] I already installed the sensors and configured them

---

### Post by m_duck on 2009-06-24
If you delete the two "Temperatura" lines the error should be gone. It is probably because your computer doesn't display its temperatures in the same way as the person whose config you used. Did you install lm_sensors? If so can you post the output of ***sensors** *in the terminal? Then we can see about displaying some temps in your conky.

---

