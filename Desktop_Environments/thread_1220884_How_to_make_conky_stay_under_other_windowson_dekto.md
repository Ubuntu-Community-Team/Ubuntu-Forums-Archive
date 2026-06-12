---
title: "How to make conky stay under other windows/on dektop?"
date: 2009-07-23
forum: Desktop Environments
---

### Post by vickoxy on 2009-07-23
Hi,
i installed conky but it keeps going over all windows. Is there a posibility to put him staying only on desktop? And is there real transparency for it?

Thanks

---

### Post by wojox on 2009-07-23
This is what I use and it stays:

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

---

### Post by vickoxy on 2009-07-23
> **wojox said:**
> This is what I use and it stays:

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

And where do you add this lines?

---

### Post by wojox on 2009-07-23
In your home directory in .conkyrc file.

---

### Post by vickoxy on 2009-07-23
Thanks - that did the job-but now every time i tab on desktop conky dissapears... :confused:

---

### Post by m_duck on 2009-07-23
Try changing ** own_window_type override **to ***normal*** or ***desktop*** (instead of override). One of those should fix it, though I've not used conky for a while.

---

### Post by vickoxy on 2009-07-23
> **m_duck said:**
> Try changing ** own_window_type override **to ***normal*** or ***desktop*** (instead of override). One of those should fix it, though I've not used conky for a while.

Ok, so if i add *normal* it stays-but with normal programm frame-which i do not want. If i add *desktop* i dissapears after clicking on desktop.


So, this is my config file:

# Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2007 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
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
# $Id: conky.conf 1193 2008-06-21 20:37:58Z ngarofil $

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
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_type desktop
own_window_transparent yes
# own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer no
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
 / $color${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} k/s${color grey} - Down:$color ${downspeed eth0} k/s
$hr
${color grey}Name                  PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

---

### Post by m_duck on 2009-07-23
Uncommenting the following line and using own_window_type normal works on my machine... Though it's entirely possible I've misunderstood the problem! ```
 # own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

---

### Post by vickoxy on 2009-07-23
> **m_duck said:**
> Uncommenting the following line and using own_window_type normal works on my machine... Though it's entirely possible I've misunderstood the problem! ```
 # own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

I tried all that but nothing. Only "desktop" helps, but there is than the frame...

---

### Post by m_duck on 2009-07-23
What frame are you referring to? Could you post a screenshot? Unless you are referring to a shadow around it? If so, that is due to Compiz (I think). There is something in the compiz manager (***sudo apt-get install compizconfig-settings-manager ***then run ***ccsm***) which must be changed to stop the shadow drawing. I don't use compiz so not sure what it is but it has been brought up a lot so a quick search of the forum should bring the answer.

---

### Post by vickoxy on 2009-07-23
So here are pics:

**Picture 1** is how i want it to be-but when i click on dekstop conky goes away...

**Picture 2** with *own_window_type normal* - everything works just fine but i do not want that standard grey applications frame around

---

### Post by VCoolio on 2009-07-23
If you have dropshadows around conky that you want gone then in ccsm go to window decorations plugin, add "!(class=Conky)" to shadow windows entry.

If conky disappears on clicking desktop or show desktop button, in ccsm go to general options and uncheck "Hide Skip Taskbar Windows" option.

---

### Post by m_duck on 2009-07-23
Hmm, that shouldn't happen if this line is in your .conkyrc (but must be uncommented, ie no # at the beginning of the line)```
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```The modified config of yours that I have tried is:```
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
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer no
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
${color grey}Processes:$color $processes ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
/ $color${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} k/s${color grey} - Down:$color ${downspeed eth0} k/s
$hr
${color grey}Name PID CPU% MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
```That config displays as my screenshot below.

---

### Post by vickoxy on 2009-07-23
m-duck, i do not know what you did-i copied your pasted conf file, and now it works as it should. :popcorn: 

Only i noticed that sometimes it blinks more noticable-is there any fix?

---

### Post by vickoxy on 2009-07-23
Ok, there is still one issue-maybe i am asing too much from conky-when i tab "show desktop" it dissapears with other programs. I should manually minimize all other windows so that conky stays on desktop...

---

### Post by vickoxy on 2009-07-23
> **VCoolio said:**
> If you have dropshadows around conky that you want gone then in ccsm go to window decorations plugin, add "!(class=Conky)" to shadow windows entry.

If conky disappears on clicking desktop or show desktop button, in ccsm go to general options and uncheck "Hide Skip Taskbar Windows" option.

I tried ccsm, but nothing...

---

### Post by m_duck on 2009-07-23
Hmm, you are not asking too much, and there are answers... Like I said, I'm a bit rusty!

For the flickering issue, add the following above **TEXT** in your config:```
double_buffer yes
```For the minimising with the show desktop button, change **own_window_type** back to **override** and it should be fine. I've just rechecked it here and it seems to work :oops:.

Conky is a strange beast, sometimes when I swear my config is right, but not working I can change it for an almost identical one and it will be fine.

---

### Post by vickoxy on 2009-07-23
Thanks, guys, especialy to you m_duck!!! NOW, all works as it should be. 

So, if someone need basic conf file for conky, this is what works for me:

> # Conky, a system monitor, based on torsmo
#
# Any original torsmo code is licensed under the BSD license
#
# All code written since the fork of torsmo is licensed under the GPL
#
# Please see COPYING for details
#
# Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
# Copyright (c) 2005-2007 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
# All rights reserved.
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
# You should have received a copy of the GNU General Public License
# along with this program. If not, see <http://www.gnu.org/licenses/>.
#
# $Id: conky.conf 1193 2008-06-21 20:37:58Z ngarofil $

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
font 6x10
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 3.0
uppercase no
use_spacer no
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
${color grey}Processes:$color $processes ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
/ $color${fs_free /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} k/s${color grey} - Down:$color ${downspeed eth0} k/s
$hr
${color grey}Name PID CPU% MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

---

### Post by vickoxy on 2009-07-23
Ok, one  last question. What was actually wrong with my .conkyrc file?
I saw on web lot of beautiful conky .conkyrc themes, but i do not want to experiment with them if i do not know what to change to make them work. Maybe, stupid question, but i am just learning linux...

Once again-thanks!

---

### Post by m_duck on 2009-07-23
The main part that was missing most of the time was the own_window_hints line. This is what removes the frame around the conky and allows it to display as if it was part of the wallpaper. It is mainly GNOME that causes problems with conky because of the way nautilus manages the desktop so all of these extra bits are added.

The other bits, such as double buffer are just tweaks to make it run better. There are a whole host of other settings which can be used to define how conky behaves. See the following:

[Conky Settings]("http://conky.sourceforge.net/config_settings.html") - These go before TEXT in your config and define how things are displayed.
[Conky Variables]("http://conky.sourceforge.net/variables.html") - These go after TEXT in your config and display different bits on information.

The best way to learn with conky is just try stuff and see if it works/what it does. Make a backup of your working conky first so you can just restore it if things go haywire, then just keep tweaking until you get something you like. Check the link in my sig for a massive thread with a multitude of different configs.

Any other questions, feel free to ask :D

---

### Post by vickoxy on 2009-07-24
> **m_duck said:**
> The main part that was missing most of the time was the own_window_hints line. This is what removes the frame around the conky and allows it to display as if it was part of the wallpaper. It is mainly GNOME that causes problems with conky because of the way nautilus manages the desktop so all of these extra bits are added.

The other bits, such as double buffer are just tweaks to make it run better. There are a whole host of other settings which can be used to define how conky behaves. See the following:

[Conky Settings]("http://conky.sourceforge.net/config_settings.html") - These go before TEXT in your config and define how things are displayed.
[Conky Variables]("http://conky.sourceforge.net/variables.html") - These go after TEXT in your config and display different bits on information.

The best way to learn with conky is just try stuff and see if it works/what it does. Make a backup of your working conky first so you can just restore it if things go haywire, then just keep tweaking until you get something you like. Check the link in my sig for a massive thread with a multitude of different configs.

Any other questions, feel free to ask :D

Thanks for help-found after your signature lot of help and beautifull functional conky files... :popcorn:

---

