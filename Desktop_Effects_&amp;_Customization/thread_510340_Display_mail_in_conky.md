---
title: "Display mail in conky"
date: 2007-07-26
forum: Desktop Effects &amp; Customization
---

### Post by Tuning_In on 2007-07-26
Hi!

I'm new to conky and have troubles with displaying the "mail" as shown in the [COLOR="Red"][post]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+script&page=15")[/COLOR]
by LoKe. 

This is my .conkyrc

> background yes
use_xft no
xftfont Bitstream Vera Sans:size=7
xftalpha 0.8
update_interval 0.5
own_window yesEdit/Delete Message  
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_border no
draw_graph_borders yes
stippled_borders no
default_color white
default_shade_color black
alignment top_right
minimum_size 1425
maximum_width 1050
gap_y 32
gap_x 32
use_spacer no
no_buffers yes

TEXT
${color white} Processors - Intel Core2 Duo - ${cpu cpu0}% ${cpugraph cpu1 8, 30 ffffff ffffff} ${cpugraph cpu2 8, 30 ffffff ffffff} | Memory - ${mem} of ${memmax} ${memgraph mem 8, 30 ffffff ffffff} | Processes - $running_processes of $processes running | HDD - ${fs_used /} of ${fs_size /} used | Email: ${color 95956B}${execi 300 python ~/.conky/gmail.py} ${color FFFFFF} 

I'm not shure what to do, but do I have to download the gmail.py file from somewhere and put it in the conky dir or something? 

Thanks in advance:)

---

### Post by Tuning_In on 2007-07-26
EDIT: 
Also, is it possible to show the songs I play in Amarok?

---

