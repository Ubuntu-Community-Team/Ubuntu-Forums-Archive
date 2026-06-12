---
title: "Conky Font Loading Issues"
date: 2009-07-24
forum: Desktop Environments
---

### Post by .Masochist on 2009-07-24
EDIT: Sorry about the title, I figured that font bit out so now its just general Conky issues. 


Hey guys,

I'm trying to load the code:

```
alignment top_left
background yes
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 0.5
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
alignment top_left
gap_x 10
gap_y 10
no_buffers no
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer yes
text_buffer_size 256

TEXT
${color 740E0E}${font Futura LT Condensed:size=100}${voffset -30}${time %I}${color 000000}${font Futura LT Condensed:size=100}${time :%M%p}
${offset 380}${voffset -210}${color 000000}${font Futura LT Condensed:size=50}${time %A}
${offset 380}${voffset -29}${color 740E0E}${font Futura LT Condensed:size=50}${time %d}${color 000000}${font Futura LT Condensed:size=50}${time %B}${font Verdana:size=0}

   

```This was taken from someone's code in the Conky scripts/pics thread. 

When I try to load it I get the output:

k@k-desktop:~$ conky -c ~/Conky/conkymain
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: forked to background, pid is 24633
k@k-desktop:~$ 
Conky: desktop window (14000a8) is subwindow of root window (1a7)
Conky: window type - normal
Conky: drawing to created window (0x3800001)
Conky: drawing to double buffer


My issue currently is I cannot get this to display at all. Is it just alignment issues?

Thank you very much!

---

### Post by .Masochist on 2009-07-24
Sorry ignore.

---

