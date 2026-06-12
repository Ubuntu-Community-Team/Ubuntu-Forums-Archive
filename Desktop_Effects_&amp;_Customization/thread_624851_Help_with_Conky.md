---
title: "Help with Conky"
date: 2007-11-27
forum: Desktop Effects &amp; Customization
---

### Post by Ub1476 on 2007-11-27
As you see on the picture, Conky's window has a small shadow around it. Also the window itself is rather large. Is there anyway I can make it smaller or remove the shadow (or make it smaller)?

Here's my conkyrc:

```

#avoid flicker
double_buffer yes
no_buffers yes
 
#own window to run simultanious 2 or more conkys
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorate,sticky,skip_taskbar,skip_pager
  
#borders
#draw_borders no
#border_margin 1
  
#shades
draw_shades no
#draw_graph_borders yes
#draw_borders yes
  
position
gap_x 1
gap_y 788
alignment bottom_left
  
behaviour
update_interval 1
  
#colour
default_color 000000
#default_color D6D6D6
#default_color bfbfbf
#default_shade_color 000000
own_window_colour 202020
#draw_borders_colour 000000
#draw_graph_borders_colour 000000
#484432 95956B
  
#font
use_xft yes
xftfont HandelGotD:pixelsize=10
  
#to prevent window from moving
use_spacer no
minimum_size 1278 10
 
#mpd
mpd_host localhost
mpd_port 6600
# ${offset -22}
TEXT
${voffset -1} Cpu: ${color 225E00}${font}${cpu}% ${color 292929}${color} P: ${color 225E00}${font}${processes}${color} R: ${color 225E00}${font}${running_processes}${color 292929} |${color} Mem: ${color 225E00}${font}${mem}${color} Swap: ${color 225E00}${font} ${swap} ${color 292929} | ${color} Uptime: ${color 225E00}${font}${uptime_short}${color 292929} | ${color 225E00}${font}${downspeed eth1} Kb/s ${color} ${totaldown eth1} down${color 292929}  | ${color} ${color 225E00}${upspeed eth1} Kb/s ${color} ${totalup eth1} up${color 292929}  |  ${color}Size: ${color 225E00}${font}${fs_size /} ${color} Left: ${color 225E00}${font}${fs_free /home/kasper} ${color 292929}|  ${color} Battery:${color 225E00} ${battery}${color} |  Temp: ${color 225E00}${font}${acpitemp}${color}C ${color 292929} | ${color 225E00}${color} Music: ${color 225E00}${font}${execi 10 exaile --get-title} - ${execi 10 exaile --get-artist} ${execi 10 exaile --get-status}${color 225E00}${alignr}${color}${time %A, %d %B} ${color}${time  %H:%M}

```

---

### Post by psyopper on 2007-11-27
Are you using Compiz and/or Desktop Effects? Conky presents as a standard window by default (at least to Compiz) so Compiz / Desktop Effects will shadow it automatically. 

You need to exclude Conky in CCSM under Window Borders. If you are using standard GUtsy Desktop Effects you will need to install CompizConfig Settings Manager:
```

sudo aptitude install compizconfig-settings-manager

```

You can access CCSM through System-Preferences

---

### Post by Ub1476 on 2007-11-27
Hi and thanks for reply. 

Currently "Shadow for windows" is set to any. How can I exclude Conky without removing "any"?

---

### Post by psyopper on 2007-12-05
Use the [Window Matching Rules]("http://wiki.compiz-fusion.org/WindowMatching") to exclude Conky. It would be something like:

```

!name=conky

```

Any *should* be a default, so using the above with nothing else should exclude Conky while still shadowing everything else.

---

### Post by rjmdomingo2003 on 2008-01-03
> **Ub1476 said:**
> As you see on the picture, Conky's window has a small shadow around it. Also the window itself is rather large. Is there anyway I can make it smaller or remove the shadow (or make it smaller)?

Here's my conkyrc:

```

#avoid flicker
double_buffer yes
no_buffers yes
 
#own window to run simultanious 2 or more conkys
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorate,sticky,skip_taskbar,skip_pager
  
#borders
#draw_borders no
#border_margin 1
  
#shades
draw_shades no
#draw_graph_borders yes
#draw_borders yes
  
position
gap_x 1
gap_y 788
alignment bottom_left
  
behaviour
update_interval 1
  
#colour
default_color 000000
#default_color D6D6D6
#default_color bfbfbf
#default_shade_color 000000
own_window_colour 202020
#draw_borders_colour 000000
#draw_graph_borders_colour 000000
#484432 95956B
  
#font
use_xft yes
xftfont HandelGotD:pixelsize=10
  
#to prevent window from moving
use_spacer no
minimum_size 1278 10
 
#mpd
mpd_host localhost
mpd_port 6600
# ${offset -22}
TEXT
${voffset -1} Cpu: ${color 225E00}${font}${cpu}% ${color 292929}${color} P: ${color 225E00}${font}${processes}${color} R: ${color 225E00}${font}${running_processes}${color 292929} |${color} Mem: ${color 225E00}${font}${mem}${color} Swap: ${color 225E00}${font} ${swap} ${color 292929} | ${color} Uptime: ${color 225E00}${font}${uptime_short}${color 292929} | ${color 225E00}${font}${downspeed eth1} Kb/s ${color} ${totaldown eth1} down${color 292929}  | ${color} ${color 225E00}${upspeed eth1} Kb/s ${color} ${totalup eth1} up${color 292929}  |  ${color}Size: ${color 225E00}${font}${fs_size /} ${color} Left: ${color 225E00}${font}${fs_free /home/kasper} ${color 292929}|  ${color} Battery:${color 225E00} ${battery}${color} |  Temp: ${color 225E00}${font}${acpitemp}${color}C ${color 292929} | ${color 225E00}${color} Music: ${color 225E00}${font}${execi 10 exaile --get-title} - ${execi 10 exaile --get-artist} ${execi 10 exaile --get-status}${color 225E00}${alignr}${color}${time %A, %d %B} ${color}${time  %H:%M}

```
Your conky's not displaying HandelGotD font.

---

### Post by u-blunt-2 on 2008-01-29
I have same problem. Similar conkyrc, except "own_window_type override".  (I have also tried Desktop, same problem).
adding !name=conky to window decorating exclusion didn't work. 
Any other suggestions ?

---

### Post by u-blunt-2 on 2008-01-29
Problem solved:

in CSSM -> Window decoration

add "-conky" to Shadow windows. Should be "any -conky".

---

