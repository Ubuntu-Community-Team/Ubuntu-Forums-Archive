---
title: "First Conky Script almost complete...slight problem"
date: 2007-12-11
forum: Desktop Effects &amp; Customization
---

### Post by Lotekx on 2007-12-11
Hi, I am trying to make a conky script that is a single line at the top of my screen and is over my panel/taskbar. No matter what I try, the display is always under the taskbar, or below it. Is there any way I can change this?

Here is my script so far:


#3F4243


# set to yes if you want Conky to be forked in the background
background no


#avoid flicker

double_buffer yes



#own window to run simultanious 2 or more conkys

own_window  yes

own_window_transparent yes

own_window_type override

own_window_hints undecorate,sticky,skip_pager 



#borders

draw_borders no

border_margin 1



#shades

draw_shades no



#position

gap_x 15

gap_y 15

alignment top_left



#behaviour

update_interval 1



#colour

default_color  858ED0



#default_shade_color 000000

own_window_colour 3d352a



#font

use_xft yes

xftfont bauhaus:pixelsize=14



#to prevent window from moving

use_spacer no

minimum_size 1262 0





TEXT

| ${time %d %B} ${color D7D3C5}${time  %H:%M}  |  ${color} Up: ${color D7D3C5}${uptime_short}   |   ${color}Processes: ${color D7D3C5}${processes}  ${color}Running: ${color D7D3C5}$running_processes   |  ${color}Cpu: ${color D7D3C5}${cpu}%   ${color}${cpugraph 10,80 AEA08E 9F907D} ${color D7D3C5}  |  ${color }Mem: ${color D7D3C5}$mem/$memmax - ${memperc}% ${color} ${membar 6,80}${color D7D3C5}    |   ${color }Net: ${color D7D3C5}${font}${downspeed eth1} Kb/s ${color}  ${downspeedgraph eth1 10,80 AEA08E 9F907D}  ${color D7D3C5} ${totaldown eth1} down   |   ${color D7D3C5}${upspeed eth1} Kb/s ${color} ${upspeedgraph eth1 10,80 AEA08E 9F907D}  ${color 909090}${totalup eth1} up |  ${color} Home: ${color D7D3C5}${fs_free /home}  / ${fs_size /home}  - ${fs_free_perc /home}%  |

---

