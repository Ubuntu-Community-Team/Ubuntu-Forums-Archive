---
title: "Help with my conkyrc"
date: 2009-01-14
forum: General Help
---

### Post by OinkOink2 on 2009-01-14
Hi all,

Being new to Python I could use a little help with my conky file.

I originally downloaded it but some parts of it I did'nay like so I altered areas by deleting and adding code in others. One particular addition I made to the code was adding the LCD-like clock which you can see in the screenshot. What I'm looking for is to get the clock much closer to my CPU bar, preferable the same distance as is the first embedded terminal to the signal bar below the up- and downstream graphs - see [COLOR="Red"]red[/COLOR] arrow.

From what I have learned I believe I need to add some ```
**${align[COLOR="Blue"]r/c[/COLOR]}**
``` and ```
**${voffset [COLOR="Blue"]value[/COLOR]}**
``` arguments in there possibly.

Also, I was wondering how I can change that icon too - see [COLOR="Green"]green[/COLOR] arrow.

Before giving my conky I would like to ask for someone to help me "tidy" it up. As I said I'm a newbie with Python so if there are arguments or bits of syntax that don't need to be there do show me where and why (so I can learn! ;) ) and then I can delete them. Here is my conky code:```

background no 
font Monospace:size=7
#xftfont Monospace:size=7
use_xft yes
xftalpha 0.9
update_interval 0.9
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 300
maximum_width 1270
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color 86A2B2
default_shade_color 002200
default_outline_color 22ee99
alignment top_left
gap_x 20
gap_y 120
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase no 

TEXT

${color white}${font led:size=50}${time %I}:${time %M}:${time %S}${font led:size=40}${time %p}${color}
${font Monospace:size=7}${goto -383}${voffset 10}${cpubar 4, 500}
${goto -383}${voffset -2}${cpugraph 80, 500 B0FCFC ECECD0}${goto 256}${voffset -70} CPU: ${cpu cpu1}% ${cpu cpu2}%
${goto 256}${voffset 8} Bat: ${battery_percent}%
${goto 256} Root: ${fs_used /} / ${fs_size /}
${goto 256} IP: ${addr eth1}
${goto 256}${voffset 9} RAM: ${memperc}% of $memmax
${goto -383}${voffset 2}${membar 4, 500}
${goto -383}${voffset -4}${downspeedgraph eth1 40, 247 ACF400 ECECD0}  ${goto 256}${upspeedgraph eth1 40, 247 FCFC6C F9F9EE}
${goto -383}${voffset -43} down: ${downspeed eth1}.0KB/s ${goto 256} up: ${upspeed eth1}.0KB/s
${goto -383} today:${execi 300 vnstat | grep "today" | awk '{print $2 $3}'} ${goto 256} today:${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}
${goto -383} month:${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'} ${goto 256} month:${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
${goto -383}${voffset 5}${wireless_link_bar 4, 500 wlan0}
${color B4BCBF}${goto -530}${voffset -147} ${top pid 1} ${top name 1}${alignr 578}${top cpu 1}${alignr 573}${top mem 1}
${color B4BCBF}${goto -530}${voffset -1} ${top pid 2} ${top name 2}${alignr 578}${top cpu 2}${alignr 573}${top mem 2}
${goto -530}${voffset -1} ${top pid 3} ${top name 3}${alignr 578}${top cpu 3}${alignr 573}${top mem 3}
${goto -530}${voffset -1 } ${top pid 4} ${top name 4}${alignr 578}${top cpu 4}${alignr 573}${top mem 4}
${color B4BCBF}${goto -530}${voffset -1} ${top pid 5} ${top name 5}${alignr 578}${top cpu 5}${alignr 573}${top mem 5}
${goto -530}${voffset -1} ${top pid 6} ${top name 6}${alignr 578}${top cpu 6}${alignr 573}${top mem 6}
${goto -530}${voffset -1} ${top pid 7} ${top name 7}${alignr 578}${top cpu 7}${alignr 573}${top mem 7}

```

---

### Post by OinkOink2 on 2009-01-14
EDIT: Btw people, what is "laptop mode on" and where can I find it to toggle it?

When I alter the battery charge line and use the argument ```
**Bat: [COLOR="Red"]0 ${battery_bar 4, 30} [/COLOR]${battery_percent}%**
```
before the battery_percent one (and given that I'm launching from terminal) I get a response from the terminal stating that it can't locate whatever due to that argument.

Is this something to do with ACPI? Because in addition to this I sometimes get similar errors from battery widgets (if not then at least an unresponsive widget!).

?

---

### Post by easybake on 2009-01-15
> **OinkOink2 said:**
> Hi all,

Being new to Python I could use a little help with my conky file.

I originally downloaded it but some parts of it I did'nay like so I altered areas by deleting and adding code in others. One particular addition I made to the code was adding the LCD-like clock which you can see in the screenshot. What I'm looking for is to get the clock much closer to my CPU bar, preferable the same distance as is the first embedded terminal to the signal bar below the up- and downstream graphs - see [COLOR="Red"]red[/COLOR] arrow.
Below the TEXT in the conkyrc in between the first 2 lines put this
```
${voffset -50}
```


> 
Also, I was wondering how I can change that icon too - see [COLOR="Green"]green[/COLOR] arrow.
[Look here]("http://ubuntuanswers.wordpress.com/2007/12/28/customizing-your-main-menu-icon-replacing-the-default-ubuntu-logo/")

---

### Post by blackened on 2009-01-15
> **OinkOink2 said:**
> EDIT: Btw people, what is "laptop mode on" and where can I find it to toggle it?...

```
sudo apt-get install laptop-mode-tools
```

then edit /etc/laptop-mode/laptop-mode.conf

---

