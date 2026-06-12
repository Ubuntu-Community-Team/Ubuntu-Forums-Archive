---
title: "Log monitoring"
date: 2009-03-19
forum: Desktop Environments
---

### Post by WhiskyChris on 2009-03-19
I have a very low volume log (a message of < 20 chars every few hours) that I would like to keep an eye on while at work. I can do tail -f in the terminal and shrink the window down to a couple of lines but I'd prefer to put the output into a small box on the task bar (appologies if that's the wrong word, I'm fairly new to ubuntu, I mean the bar traditionally at the top with the main menus and the clock etc).

Has anyone come across such an app or does anyone do something similar in a different way I've not thought of?

Thanks!

---

### Post by m_duck on 2009-03-19
I'm not sure how to do exactly as you request, but you could use the system monitor app "Conky" to display the information on the desktop. Install conky ```
sudo apt-get install conky
```After installing, you will need a config file in your home directory for it called .conkyrc. You could either start with the standard config and modify that (code shown), use one of the many configs from the conky thread in my sig, or use the config file at the end of this post.```
cp /etc/conky/conky.conf ~/.conkyrc
```Open it up in your favourite text editor (using nano as an example) as you will need to add a line for monitoring your log file```
nano ~/.conkyrc
```Somewhere you will want to add something such as```
My Log File ${hr}
${execi 60 cat /path/to/log/file | tail -n5 | fold -s -w30}
```This will read the log file every 60 seconds and output it to the desktop, wrapping the text after 30 chars, or before if that would break a word. This will display something like the screenshot below.

As long as you are not using KDE, the following .conkyrc should work fine - it will probably need to be modified if you are though. It displays the last 5 lines of the log file in the top left of the desktop.```
alignment top_left
background yes
cpu_avg_samples 2
default_color DimGray
default_outline_color green
default_shade_color red
double_buffer yes
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
gap_x 50
gap_y 50
maximum_width 300
minimum_size 300
net_avg_samples 1
no_buffers yes
override_utf8_locale yes
own_window yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type normal
text_buffer_size 512
total_run_times 0
update_interval 1.0
uppercase no
use_spacer right
use_xft yes
xftalpha 0.1
xftfont Monospace:size=8

TEXT
${color Tan2}Logging ${color Gray}${hr}
${execi 60 cat ~/logfile | tail -n5 | fold -s -w50}
```

---

### Post by WhiskyChris on 2009-03-19
Thanks for pointing me towards conky - it looks good and works a treat. I'll have a bit more of a play with it later to try and customise it and will ask back if I've got any more problems.

---

