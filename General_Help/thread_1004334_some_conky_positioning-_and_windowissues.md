---
title: "some conky positioning- and windowissues"
date: 2008-12-07
forum: General Help
---

### Post by hachel on 2008-12-07
hello there,
I have problems setting up my conky properly. First of all, this is my rc:
```
use_xft yes
xftfont verdana:size=8
alignment top_left
gap_x 500
gap_y 200
xftalpha 0.8
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 0
border_width 0
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58
text_buffer_size 2048
```
I set own_window to yes so that my desktopicons wouldn't disappear all the time, but now there is a black border all around the window (even though I have all those shades and border options set to no).
Also, I can't decide on a window_type. On "desktop" it will sit on my desktop even when I hit the "hide windows and show desktop"-button in the bottom-left corner, but once I click anywhere on the desktop, the window disappears and won't come back.
When I set it to overwrite it disappears when I click beforementioned button.
So, what should I alter to have those borders/shadows disappear (they disappear when I disable compiz) and how can I keep it on the desktop without disappearing?
thanks, 
 hachel

---

