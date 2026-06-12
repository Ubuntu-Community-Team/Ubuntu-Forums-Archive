---
title: "Cant seem to get conky to work right"
date: 2008-12-24
forum: General Help
---

### Post by fedex1993 on 2008-12-24
Right now i am working on a new conky config that has date on the left pside and the time on the right. i got the date working good on the left side but having problem with the time on the right. Here is a screeny. [http://stashbox.org/337539/2008-12-24-140305_1280x800_scrot.png](http://stashbox.org/337539/2008-12-24-140305_1280x800_scrot.png)

i want to get the 02 down to the bottom like the dec on the left side and i cant seem to get it working. Here is the config file

```
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_spacer none
use_xft yes
uppercase yes
update_interval 1.0
draw_shades no
draw_outline no
draw_borders no
stippled_borders 0
border_margin 0
border_width 0
default_color c0c0c0
own_window_transparent yes
minimum_size 1 1
maximum_width 200
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
gap_x 0
gap_y -6

TEXT
${color 0096d1}${time %I}${color}:${font Arial:bold:size=40}${color ffffff}${time %M}${color}${font}

```

---

