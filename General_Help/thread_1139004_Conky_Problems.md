---
title: "Conky Problems"
date: 2009-04-26
forum: General Help
---

### Post by zyxyellowxyz on 2009-04-26
I know others are having issues with Conky after the upgrade to 9.04, and I am one of them. Yes, I searched the forums and found an answer to one of my problems, but not the major one.

I have conky where it is supposed to start up on, well, start up. I've tried just using the command "conky" and I won't see it. I've tried the sh script
```
#!/bin/bash
sleep 10 && conky;
```
and I still won't see it.
The only way it seems that I will see Conky is if I go to the terminal and type
```
killall conky
``` (since it is technically running even if I can't see it) and then just "conky" to start it up.
I don't know what it going wrong, as it was working perfectly yesterday (before I updated last night)

This is my Conkyrc in case anyone can figure out what is wrong within it:
```
# Conky configuration

background yes
use_xft yes
xftfont Sans:size=9
xftalpha 0.8
update_interval 5.0
total_run_times 0
own_window no
own_window_type override
own_window_transparent yes
own_window_colour black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
border_margin 2
border_width 1
default_color white
default_shade_color black
default_outline_color black
alignment middle_right
gap_x 12
gap_y 0
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer none
show_graph_scale no
show_graph_range no
text_buffer_size 1024
color1 333333
color2 000000
color3 FFFFFF
color4 AAAAAA
color5 3B3B3B

# stuff after 'TEXT' will be formatted on screen

TEXT
***
```

Before anyone asks:
[LIST]
[*]Yes, I do have compiz enabled, it didn't give me a problem yesterday
[/LIST]

I would rather not have to manually start and stop it, but I guess I will if I have to.

**Edit** I didn't notice this before but now the icons on the desktop are not showing up, kind of like they are flickering/blinking.

-------------------------------------------------------------
**EDIT 05/14/2009**
I fixed this a while ago. My Conky is working fine now. I modified the SH script to wait 20 seconds instead of 10, and I don't remember how I fixed the blinking icons, but they no longer blink.

---

### Post by Dawei87 on 2009-05-06
i had this same problem using the conky sh script, only mine was set for 20 seconds and still didnt work. the only way i was able to fix it is i set it to 30 seconds and had to wait a little longer, but it worked fine on startup once i set the sleep command longer. hope this helps

edit: i didnt see your edit at the bottom, im not sure what to do about the icons, sorry

---

