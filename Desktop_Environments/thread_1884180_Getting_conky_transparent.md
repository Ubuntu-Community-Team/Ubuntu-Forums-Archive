---
title: "Getting conky transparent"
date: 2011-11-20
forum: Desktop Environments
---

### Post by murdockpt on 2011-11-20
my conky.conf

alignment top_right
background yes
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
xftfont DejaVu Sans Mono:size=12
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type desktop
own_window_transparent yes
stippled_borders 0
update_interval 0.8
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no
double_buffer yes

TEXT
${scroll 16 $nodename - $sysname $kernel on $machine | }
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
 / $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} ${color grey} - Down:$color ${downspeed eth0}
$hr
${color grey}Name              PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

basically havent changed much from the default at the moment. took some fenangling but i finally got its position correct (for some reason it would be invisible when aligned top_right)

now before i start tweaking, i would like its window to be transparent, so i added the line:

own_window_transparent yes

it did what i wanted in that it showed my desktop, but clicking anywhere on the desktop that isnt on conky makes it dissappear.

have also tried own_window no, but to no avail, as it doesnt show up.

solutions oh mighty all knowers of the ubuntu realm?

---

### Post by murdockpt on 2011-11-20
protip - ive been tweaking the conky.conf in my etc/conky location.

adding new files and whatnot to something that wasnt working only made backtracking harder. decided to change the source.

---

### Post by Frogs Hair on 2011-11-20
You could try command below , which solved the same problem with one of my themes. ```
own_window_type override
```

---

### Post by murdockpt on 2011-11-20
that only managed to make the window not show up again, so that suggestion didnt work :/ dangit

---

### Post by werewolves on 2011-11-21
No idea if this will help, but here is a section from my conkyrc.

> 
own_window yes
own_window_transparent yes
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager


---

### Post by stinkeye on 2011-11-21
To solve the disappearing issue change (as **Frogs Hair** said)
```
own_window_type desktop
```

to
```
own_window_type override
```

> **murdockpt said:**
> protip - ive been tweaking the conky.conf in my etc/conky location.
When you run conky it will first look for a conky config @ **~/.conkyrc**
If there is no config here it will load the default config @ **/etc/conky/conky.conf**

So you should copy the default config to your home folder so you can edit as a normal user.
```
cp /etc/conky/conky.conf ~/.conkyrc
```

Then just browse to the hidden **.conkyrc** file in your home folder
or in terminal 
```
gedit ~/.conkyrc
```

If you think you've messed with the default config to much
this is the original config @ **/etc/conky/conky.conf**
Save as **.conkyrc** in your home folder.
```
# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2010 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

alignment top_left
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
xftfont DejaVu Sans Mono:size=12
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type desktop
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

TEXT
${scroll 16 $nodename - $sysname $kernel on $machine | }
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
 / $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} ${color grey} - Down:$color ${downspeed eth0}
$hr
${color grey}Name              PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
```

---

