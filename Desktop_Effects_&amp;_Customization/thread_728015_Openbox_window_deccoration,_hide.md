---
title: "Openbox window deccoration, hide"
date: 2008-03-18
forum: Desktop Effects &amp; Customization
---

### Post by PurposeOfReason on 2008-03-18
Here is a screenshot for reference.
[http://purposeofreason.deviantart.com/art/03-17-2006-80298422](http://purposeofreason.deviantart.com/art/03-17-2006-80298422)

As you can tell, I've already set the window decoration font to 1 to get it as small as possible, which is nice, but I'd prefer it to all be as thick as the boarders around the window. Is there a way to remove the window decoration in openbox?

---

### Post by kerry_s on 2008-03-18
sorry, don't have an answer for you, i have a question.
what monitor is that your using in the top right side?

---

### Post by PurposeOfReason on 2008-03-18
Getting my hopes up. ;)

That is conky. The boarder is really just a box drawn on the wallpaper to hide xcompmgr shadows that can't be removed as of late. The fonts are all free on the internet, check dafont.com
My config:
```

background no
font Myraid Pro:size=7
use_xft yes
xftalpha 1.0
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 85 5
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_outline_color white
default_color 000000
alignment top_right
gap_x 60
gap_y 65
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no

TEXT
   ${font weather:size=22}${execi 600 ~/.scripts/conditions.sh}${font}${alignr 2}  ${voffset -6}${execi 600 ~/.scripts/pogodynka.sh}
   ${voffset -1}${if_existing /sys/class/power_supply/BAT1/status Discharging}${font StyleBats:size=18}o${else}${font StyleBats:size=18}p${endif}${font}${alignr 2}    ${voffset -6}${battery_percent BAT1}%
   ${voffset 1}${font PizzaDude Bullets:size=16}M${font}${alignr 2}    ${voffset -4}${if_existing /sys/class/net/eth0/operstate up}${upspeed eth0} Kb/s${else}${if_existing /sys/class/net/wlan0/operstate up}${upspeed wlan0} Kb/s${else}--${endif}${endif}
   ${voffset 2}${font PizzaDude Bullets:size=16}S${font}${alignr 2}    ${voffset -4}${if_existing /sys/class/net/eth0/operstate up}${downspeed eth0} Kb/s${else}${if_existing /sys/class/net/wlan0/operstate up}${downspeed wlan0} Kb/s${else}--${endif}${endif}
   ${voffset -1}${font FreeSans:size=16}@${font}${alignr 2}    ${voffset -3}${if_existing /sys/class/net/eth0/operstate up}${execi 300 python ~/.scripts/gmail.py}${else}${if_existing /sys/class/net/wlan0/operstate up}${execi 300 python ~/.scripts/gmail.py}${else}--${endif}${endif}
   ${voffset 2}${font PizzaDude Bullets:size=16}]${font}${alignr 2}    ${voffset -3}${texeci 10800 perl /home/shawn/.scripts/conky-updates.pl}

```

---

### Post by kerry_s on 2008-03-18
thanks, that's very slick. the images through me off. :)

---

### Post by PurposeOfReason on 2008-03-18
We're getting there, I can put ```
  <application class="*">
    <decor>no</decor>
  </application>

```
in my rc.xml, but it also gets rid of the nice green touches at the top and the bottom.

---

