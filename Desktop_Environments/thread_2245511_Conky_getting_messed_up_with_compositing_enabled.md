---
title: "Conky getting messed up with compositing enabled"
date: 2014-09-24
forum: Desktop Environments
---

### Post by linuxyogi on 2014-09-24
Hi,

After installing Cairo Dock I found that its was not working properly and a message popped up

saying I need to enable compositing for Cairo Dock to function properly.

So, after reading [this]("http://askubuntu.com/questions/53745/compositing-in-lubuntu") I added xcompmgr to startup.

Now Cairo Dock is working properly but some parts of Conky is unreadable.

Is there a way to fix this ?

Specs : AMD Athlon 64 X 2 5600 +
             Ram : 2GB
             Nvidia 6150 SE (NVIDIA Driver Version: 304.117)

Please see attachment.

[ATTACH=CONFIG]256636[/ATTACH]

---

### Post by vasa1 on 2014-09-24
If you include the actual conky code, someone could help you better.

Plus, people seem to prefer compton over xcompmgr. That AU link is quite old. We have a compton thread here: ubuntuforums.org/showthread.php?t=2144468

---

### Post by linuxyogi on 2014-09-24
```
$ cat  /etc/conky/conky.conf
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
own_window yes
own_window_class Conky
own_window_type normal 
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager  
own_window_transparent yes
# position
alignment top_right
gap_x 0
gap_y 0
TEXT
${goto 180}${color0}${font Droid Sans:style=bold:size=13}${voffset 40}${exec whoami}
${voffset -30}${font Droid Sans:style=Bold:size=12}${color}${goto 40}${uptime}
${goto 80}${color1}${font Droid Sans:style=Bold:size=12}${color1}${sysname}${color}${font}
${voffset 70}${goto 20}${font Droid Sans:style=bold:size=18}${time %a %b %d}${font}${goto 175}
${voffset 0}${goto 20}${font Droid Sans:style=bold:size=18}${time %l:%M  %p}${font}${goto 175}${font Droid Sans:style=Bold:size=11}CPUs
${goto 175}${font Droid Sans:style=Bold:size=11}${color1}${cpu cpu0}%
${goto 175}${font Droid Sans:style=Bold:size=11}${color1}${cpu cpu1}%
${voffset 35}${goto 35}/home${color1}${goto 128}SWAP
${goto 38}${font Droid Sans:style=Bold:size=10}${fs_used /home}${goto 134}${font Droid Sans:style=Bold:size=11}${swapperc}${font Droid Sans:style=Bold:size=11}${color1}${font}%
${font Droid Sans:style=Bold:size=11}${font}
${voffset 10}${goto 90}${font Droid Sans:style=Bold:size=11}RAM
${goto 90}${font Droid Sans:style=Bold:size=11}${memperc}%


```


Trying compton now.

---

### Post by vasa1 on 2014-09-24
> **linuxyogi said:**
> ```
$ cat  /etc/conky/conky.conf...
```
...So you don't have a ~/.conkyrc? I prefer ~/.conkyrc myself; one less need for sudo.

---

### Post by linuxyogi on 2014-09-24
Installed compton.

```
**sudo apt-add-repository ppa:richardgv/compton**
```

```
sudo apt-get update && sudo apt-get install compton
```

```
leafpad ~/.compton.conf
``` [ .compton.conf]("http://paste2.org/5UnMacVC")

```
$ cat ~/.config/lxsession/Lubuntu/autostart
@conky
cairo-dock
# @xcompmgr -c
@compton -b &
```

Logged out and back in. Same problem.

[ATTACH=CONFIG]256639[/ATTACH]

---

### Post by linuxyogi on 2014-09-24
> **vasa1 said:**
> So you don't have a ~/.conkyrc? I prefer ~/.conkyrc myself; one less need for sudo.

I was using ~/.conkyrc with Manjaro I just copied to /etc/conky/conky.conf.

[Official Doc]("https://help.ubuntu.com/community/SettingUpConky")

> The file can be found in /etc/conky/conky.conf.

---

### Post by vasa1 on 2014-09-24
Can you try this ~/.conkyrc?
```
# Conky, a system monitor, based on torsmo
#
#
use_spacer right

double_buffer yes
alignment top_left
background no
default_color 000005
use_xft yes
xftfont Ubuntu Mono:bold:size=16
gap_x 5
gap_y 5
minimum_size 505 150
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type desktop
own_window_type normal 
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager  
own_window_transparent no
update_interval 2.0
uppercase no
use_spacer none
#######
border_width 5

TEXT
${color 555555}${time %a, %d %b}$color ${color B3492B}${time %H:%M}$color ${color 555555}${utime (%H:%M)} ${acpitemp}${iconv_start UTF-8 ISO_8859-1}°${iconv_stop}C $color ${cpugraph 15,25 006000 006000} ${color 004000} ${cpu}%$color

```

It sits at the top-left of the screen.

---

### Post by linuxyogi on 2014-09-24
This is how its looking 

[ATTACH=CONFIG]256640[/ATTACH]

Also, compton is not auto starting despite that entry. I have start it manually.

---

### Post by linuxyogi on 2014-09-24
Problem solved. Installed Metacity.

[ATTACH=CONFIG]256641[/ATTACH]

---

