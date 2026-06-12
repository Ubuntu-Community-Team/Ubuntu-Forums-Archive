---
title: "Problems with Display after upgrade to 8.10"
date: 2009-02-11
forum: General Help
---

### Post by chamber on 2009-02-11
Ive been having some problems with my display ever since I upgraded to Intrepid.

There is now a box around my 2 conkys were there wasn't any before, It's really annoying as they were fine before.

Here is the code from the top,

```
#Conky Configuration File

maximum_width 300
background no
border_width 1
cpu_avg_samples 3
text_buffer_size 512

default_color light grey
default_outline_color light grey
default_shade_color light grey

draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no

use_xft yes
xftfont 
xftalpha 0.5
gap_x 5
gap_y 30
minimum_size 5 5
net_avg_samples 1
no_buffers yes
out_to_console no
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_title right hand side
stippled_borders 3
update_interval 2
uppercase yes
alignment top_right
double_buffer yes
# dark grey
color4 db7835
# colours
color1 light grey
color2 red

override_utf8_locale yes
```

And here is a screenshot of the problem.

---

### Post by chamber on 2009-02-16
Bump?

---

### Post by malathion on 2009-02-16
You might want to specify in the thread title that your problem is about Conky, as this will make it easier for users knowledgeable about it to find you.

---

