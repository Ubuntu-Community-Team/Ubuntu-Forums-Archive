---
title: "Repositionable and resizable translucent window (ruler like)"
date: 2016-02-25
forum: Desktop Environments
---

### Post by COUTIER_Eric on 2016-02-25
Hello,
I'm looking for a simple software that would be a simple rectangular window, without decoration but repositionable and resizable and "on top" and with customizable opacity and color.
It will be very suitable to put on top of an existing window for having a visual guide to follow a list, or other information.

I know "kruler" which is very like this with opacity settings but i'm not interested with graduations in my case...

Anyone know a soft like this ?

---

### Post by CantankRus on 2016-02-26
Conky may be suitable.
This config will give you a transparent undecorated window.
```
alignment none
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
gap_x 60
gap_y 60

own_window_type normal
own_window_hints undecorate,above 
[COLOR="#FF0000"]own_window_colour blue[/COLOR]
[COLOR="#FF0000"]own_window_argb_visual yes[/COLOR]  # enable real tranparency
[COLOR="#FF0000"]own_window_argb_value 100[/COLOR]  # argb value 0>255 0=transparent  255=opaque  
minimum_size 100 100
#maximum_width 
own_window yes
own_window_class Conky

net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no



stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

TEXT
```
Save the config as **.conkyrc** in your home directory.

Install conky and using the terminal, run "conky" which should bring up a semi-tranparent resizeable blue window
in the top left corner. The window may be very small to begin with as shown in second pic.
Use alt+left mouse to reposition.
Alt+middle mouse to resize.
See "man conky"

---

