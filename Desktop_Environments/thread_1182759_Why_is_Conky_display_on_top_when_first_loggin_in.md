---
title: "Why is Conky display on top when first loggin in ??"
date: 2009-06-09
forum: Desktop Environments
---

### Post by pappo on 2009-06-09
When I first log into my Ubuntu 9.04 machine, Conky comes up just as I setup but the display is "on top", meaning it covers up any windows that are put over it.
If I "killall conky" and restart Conky, it comes up as a background app and any windows I move over to it will be on top of the Conky data.

Here is the top of my .conkyrc file:

    background yes
    use_xft yes
    xftfont 123:size=8
    xftalpha 0.1
    update_interval 0.5
    total_run_times 0
    own_window yes
    own_window_type override
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 300 5
    maximum_width 200
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders no
    default_color gray
    default_shade_color red
    default_outline_color green
    alignment top_right
    gap_x 15
    gap_y 30

---

### Post by reeseslover531 on 2009-06-09
yeah this is an issue conky if it starts up before other things. Instead of runnning conky at startup run this script ```
 
#!/bin/sh
sleep 20
conky &

```
this waits for 20 seconds before it starts conky up.  That is what I did and it worked for me, good luck!

---

### Post by pappo on 2009-06-10
Thanks for the tip.  I will try it out.

---

