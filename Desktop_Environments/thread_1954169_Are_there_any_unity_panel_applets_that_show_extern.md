---
title: "Are there any unity panel applets that show external IP address"
date: 2012-04-07
forum: Desktop Environments
---

### Post by residualbit on 2012-04-07
I came accross giplet, but that doesn't seem to agree with unity. Does anyone know of any others? I'm currently on 12.04

Thanks.

---

### Post by stinkeye on 2012-04-07
Don't know of an indicator that shows external ip in the panel but you 
could use conky to display just under the panel.
```
sudo apt-get install conky-all curl
```

Save this as **.conkyrc** in your home folder.(include the preceding dot)
```
update_interval 2
total_run_times 0
net_avg_samples 1
cpu_avg_samples 1

imlib_cache_size 0
double_buffer yes
no_buffers yes

use_xft yes
xftfont Monospace:size=10
override_utf8_locale yes
text_buffer_size 2048

own_window yes
own_window_colour black
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent no
#own_window_argb_visual yes
#own_window_argb_value 50

alignment tr
gap_x 10
gap_y 50
minimum_size 100
maximum_width 0
border_inner_margin 0
border_outer_margin 0


default_bar_size 70 8
draw_shades no
default_color white
short_units yes

TEXT
${font}External IP: ${execi 60 curl ifconfig.me}
```

To test in the terminal
```
conky
```


Add to startup applications using in the command box...
```
conky -p 60
``` 
The [COLOR="DarkOrange"]-p[/COLOR] delays the start of conky for 60 secs.(so you wont see for 1 minute after logging in)


This line in .conkyrc sets the curl command to run every 60 secs.
```
${font}External IP: ${execi [COLOR="Magenta"]60[/COLOR] curl ifconfig.me}
```


Because of a bug in the conky package for 12.04 where execi commands
wont run until the update interval is greater than your computer uptime I have set the
[COLOR="magenta"]update interval[/COLOR] to a low 60 secs
and delayed the start of conky by 60 secs with the [COLOR="darkorange"]-p[/COLOR] command in
startup applications.

---

