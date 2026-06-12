---
title: "can't get my conky background transparent!"
date: 2012-08-31
forum: Desktop Environments
---

### Post by scottr99 on 2012-08-31
Hi, this is my conky.  Despite what you see here I am not getting a transparent background.  Can someone tell me why pls.  Thank you!

```
background no
font Zegoe Light:size=8
xftfont Zegoe Light:size=8
use_xft yes
xftalpha 0.6
update_interval 1
total_run_times 0
net_avg_samples 2
override_utf8_locale yes
double_buffer yes
no_buffers yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
draw_shades yes
draw_outline yes
draw_borders no
draw_graph_borders no
use_spacer none
minimum_size 280
maximum_width 1475
default_color white
default_shade_color black
default_outline_color FFFF00
draw_outline no
alignment top_right
gap_x 12
gap_y 35
text_buffer_size 2048
imlib_cache_size 0
```

---

### Post by Petro Dawg on 2012-09-01
Change "override" to "normal".  Maybe that will work.

---

### Post by Frogs Hair on 2012-09-01
Do you mean the entire window or just the edges ? I have used and modified that theme on Ubuntu and it does appear transparent except  for the outline.

---

### Post by scottr99 on 2012-09-01
Unfortunately 'normal' didn't help.  Frogs hair it's the entire conky background.

---

### Post by stinkeye on 2012-09-01
Never used kde but have seen a lot of threads about conky transparency
in KDE.
No idea if this solution works.
[**_[COLOR="DarkRed"]http://conky.pitstop.free.fr/wiki/index.php5?title=Conky_KDE_Transparency_(en)[/COLOR]_**]("http://conky.pitstop.free.fr/wiki/index.php5?title=Conky_KDE_Transparency_(en)")

Further help.... post where the conky gurus hangout.
[**_[COLOR="darkred"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=2046")

---

### Post by Petro Dawg on 2012-09-01
I'm fairly new to conky, but my transparency code works.  You might want to try to match your settings to mine as a start and then adjust one by one to get it back to how you like it.  Here are my declarations...

```
#conky performance settings
  use_xft yes
  xftalpha 0.9
  update_interval 3.0
  total_run_times 0
  cpu_avg_samples 4
  no_buffers no
  double_buffer yes
  override_utf8_locale no

#overall position of conky window
  alignment bottom_right
  gap_x 12
  gap_y 35
  minimum_size 180 5
  maximum_width 180

#overall appearance of conky window
  own_window yes
  own_window_type normal
  own_window_transparent yes
  own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
  draw_borders no

#default text apperance
  font Ubuntu:bold:size=11
  default_color khaki1
  draw_shades yes
  draw_outline yes
  default_shade_color white
  default_outline_color black
  uppercase no

#border around graphs
  draw_graph_borders yes
```

I also noticed you have "draw_outline yes" and then later you have "draw_outline no",  I think you only need that once.

---

