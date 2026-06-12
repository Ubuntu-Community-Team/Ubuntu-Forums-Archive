---
title: "Problem with conky in 9.04"
date: 2009-04-25
forum: General Help
---

### Post by prominance on 2009-04-25
I've never had a problem with conky overlapping windows until I recently upgraded to 9.04.  Now when I use 'override' for own_window_type conky will overlap any windows/applications I have up, but when I use 'desktop' for own_window_type conky will disappear when I click anywhere on the desktop.  I will include my .conkyrc file that was working fine with 8.10 but for some reason is malfunctioning with the new distro.  

Any help / suggestions would be much appreciated!


```
background yes
use_xft yes
xftfont Sans:size=8
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 200
maximum_width 200
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color white
alignment top_right
gap_x 12
gap_y 26
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
...


```

---

### Post by VCoolio on 2009-04-25
try normal for window type; it the last of three options so just see what happens.

---

### Post by prominance on 2009-04-25
Aha, what a brilliant suggestion!  After doing so this resulted in the desired behavior. Thank you very much for the help.  conky is no longer overlapping windows, nor is it disappearing when I click on the desktop somewhere.  The only difference that I have noticed thus far is when I click on the show desktop icon conky seems to minimize/hide and upon re-clicking the show desktop icon it will reappear.  This is definitely not a big deal and as long as its not overlapping and not disappearing I am happy.  

Thanks a lot for your suggestion, sorry I didn't try that before posting!

---

### Post by myxiplx on 2009-04-30
I had a similar problem, and override works fine for me in 9.04.  I don't have compiz enabled though, so I wonder if you do.  Have you seen this thread with a fix for the minimize problem in compiz?

[http://ubuntuforums.org/showthread.php?p=7158077](http://ubuntuforums.org/showthread.php?p=7158077)

---

### Post by accio on 2009-05-09
Hi, this is my first post.

I had a very similar problem: conky was starting at startup and it was overlapping all windows. But with a kill and a restart of conky problem looks fixed.. so I made this silly workaround:

I made a start script for conky and putted it in the startup list as follow:

```
#!/bin/bash
sleep 10
conky

```Conky is starting right as in the previous release :D

Hope this helps

---

