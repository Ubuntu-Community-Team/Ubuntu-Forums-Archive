---
title: "Bash conky + deluge"
date: 2009-05-10
forum: General Help
---

### Post by nmjcman101 on 2009-05-10
I'm trying to make a menu shortcut to deluge, so that when I run it, it also opens conky displaying deluge information.  I got it to work with Rhythmbox using the code:
```
#!/bin/bash
rhythmbox %U | conky -c /home/douglas/.conky/conkymusic
```but when I try to do that same thing with deluge my conky creates itself, and deluge takes a bit longer to start, so the effect is that when deluge starts the conky file is now hidden at the bottom left of the screen.  I couldn't figure out how to get it to sleep for the time required to start deluge.  Also, this is the conkyrc (I'm using the conkydeluge posted here: [html]http://ubuntuforums.org/showthread.php?t=946664[/html])
```
background yes
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval .5
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
alignment bottom_left
gap_x 10
gap_y 10
no_buffers no
uppercase no
cpu_avg_samples 4
net_avg_samples 1
override_utf8_locale yes
use_spacer right
text_buffer_size 10000

TEXT

${font Arial:bold:size=10}${color Tan1}TORRENTS ${color DarkSlateGray}${hr 2}
$font${color White}${execi 0.5 conkyDeluge | fold -w45}
```Thanks in advance.

---

