---
title: "Conky transparency not working with Compiz."
date: 2009-03-27
forum: General Help
---

### Post by racerraul on 2009-03-27
I am not able to get the Conky transparency feature to work, despite plugin into the .conkyrc file what I think is needed from research.

I am stumped... 

System Details.
OpenGEU 8.10 (Ubuntu 8.10 \ E17 WM)
Using Ecomorph session (running Compiz)

here is my file...

```
background yes
use_xft yes
xftfont HandelGotD:size=10
xftalpha 0.1
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 300 5
maximum_width 300
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 18
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale yes
use_spacer yes

TEXT


```

---

### Post by racerraul on 2009-03-27
Bump :)

---

### Post by racerraul on 2009-03-29
Ttt

---

### Post by racerraul on 2009-03-29
Got it working...

I just wasn't getting the whole pseudo transparency bit.  Went into gnome properties and set the background to be the same as Enlightenment's and the transparency is now working.

Then I found out that with some of my busy backgrounds, the transparency didn't seem like a good idea, but with it being a fake transparency, you can edit the area of the background conky sits on and via gimp edit conky's tranparency to control your opacity, save it and use the edited background in gnome for conky to use...

a bit more involved but gets the job done...

---

### Post by stanca on 2009-10-03
I found it out in the same way too,even in Elive.It's a E17 bug I heard.Gsetroot does a good job too.

---

