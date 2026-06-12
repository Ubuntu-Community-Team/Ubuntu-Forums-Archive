---
title: "[SOLVED] How do I change Conky font?"
date: 2008-12-24
forum: General Help
---

### Post by Valok on 2008-12-24
So this is my conky setup that someone over on the community forums made for me.  The one thing I want to change about it is the font, which I want to be URW Gothic L Book.  I've tried a few different things but none seem to change the font to the one I want.

```
background yes
use_xft yes
xftfont :size=8
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
alignment bottom_left
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

${color lightGreen} ${font :size=30}$alignc${time %H:%M}
${voffset -30}${font :bold:size=10}$alignc${time %d %b. %Y}
${font :bold:size=8}$alignc${time %A}
$endif 
```

Anyone know what I should change to change the font?

---

### Post by tuxxy on 2008-12-24
Did you specify the font in the conkyrc? try it for example;

```
xftfont (font) :size=8
```

---

### Post by Valok on 2008-12-24
Just gave that a try but nothing seems to have changed

---

### Post by Valok on 2008-12-24
Any other ideas?  I still can't get it to work.

---

### Post by I wanted to leave on 2008-12-24
As an example,

```
xftfont Bitstream Vera Sans:size=8
```

I believe this is what tuxxy was getting at with 

```
xftfont (font) :size=8
```

where you should've inserted a (font) of your liking

---

### Post by Valok on 2008-12-25
Hmm, maybe its just a problem with the name of my font.  I've typed in exactly that a few times and nothing is changing.

*Edit* I tried a couple other fonts to see if it was just the one, and I can't seem to change it to any font at all.

---

### Post by I wanted to leave on 2008-12-25
```
background yes
use_xft yes
[COLOR="Red"]xftfont Bitstream Vera Sans[/COLOR]:size=7.5
xftalpha 0.8
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_colour black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades yes
draw_outline yes
draw_borders no
draw_graph_borders no
stippled_borders no
border_margin no
border_width no
default_color F2ECDE
default_shade_color black
default_outline_color black
alignment bl
minimum_size 1280
gap_x 0
gap_y 25
no_buffers yes
uppercase yes
cpu_avg_samples 1
net_avg_samples 1
override_utf8_locale no
use_spacer none


TEXT
${alignc}$sysname $kernel on $nodename ${freq}Mhz ${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} | $uptime_short uptime at $cpu% cpu load with ${mem}b of ${memmax}b ($memperc%) used by $processes processes | Swap Usage: $swap/$swapmax - ($swapperc%)
${alignc}${fs_used /}b of ${fs_size /}b root partition used, ${fs_used /home}b of ${fs_size /home}b home partition used | ${downspeed eth0} kbps down (${totaldown eth0}b total) ${upspeed eth0} kbps up (${totalup eth0}b total) on ${addr eth0}
```

This is the conkyrc that I currently use...
Note the line highlighted in red :)

You will also need to restart conky for the changes to take effect

---

### Post by Valok on 2008-12-25
Found the solution!  In order to change the font I had to put the font change in that you suggested, then I also had to go into the "TEXT" section on the bottom and make that same change in each of the lines of code that tells conky what to display.

---

