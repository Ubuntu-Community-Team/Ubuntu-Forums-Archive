---
title: "[SOLVED] Conky update_interval question"
date: 2008-12-11
forum: General Help
---

### Post by richaoj on 2008-12-11
I have searched around for this, but guess I am just not so sure if and how this could be done.  First off: here is my .conkyrc file:

```

use_xft yes
xftfont verdana:size=8
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
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58
update_interval 1.0



TEXT
 ${color 6694B2}${font OpenLogos:size=45} u t
${color BADCDD}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   ${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    
   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth1} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth1} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth1}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth1}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color F8DF58}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py richaoj aorpojdr 3}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}



```

The question I have, is that if I put an update_interval at 1.0 as it is, i am pretty sure it is running the weather script every second.  (pogodynka).  I don't really want that to happen as it is a drain on resources and is completely unecessary.  However, if i set the update_interval to higher than 1.0, the cpu info and other info does not update as I would like it to.  

Is there anyway to set seperate update intervals for the different parts of conky so as to have a happy medium?

Thanks for your replies . . .

---

### Post by richaoj on 2008-12-11
I solved this problem by switching scripts to conkyforecast.  pogodynka was definantly not in english and i couldn't edit the script --- conkyforecast works much better . . .

---

