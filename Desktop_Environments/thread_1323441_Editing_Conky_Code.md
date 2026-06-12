---
title: "Editing Conky Code"
date: 2009-11-11
forum: Desktop Environments
---

### Post by PeteyPete on 2009-11-11
Can anyone give me an idea on how I can go about editing this conky code to make the panel more narrow.  Using my laptop, it's taking a third of my screen up and would like to make it a little thinner.  Here is the code:

```
# UBUNTU-CONKY
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 200 800

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

text_buffer_size 1024

# stuff after ‘TEXT’ will be formatted on screen

TEXT
$color${font arial:size=9}
$nodename@$sysname $kernel on $machine${font arial:size=8}
Battery ${battery_bar 6 BAT0}

${color orange}CPU $color
${freq}MHz${alignr}Load: ${loadavg}
${alignr}${loadgraph 20,250 e5e5e5 F1AA0E}
CPU Total:${color} ${cpu cpu0}% ${color}${alignr}Temp:${color} ${acpitemp}
${alignr}${cpugraph 0 20,250 e5e5e5 F1AA0E}
Core one: ${color}${cpu cpu1}% ${alignr} Core two: ${color}${cpu cpu2}%
${cpugraph 1 20,120 e5e5e5 F1AA0E}${alignr}${cpugraph 2 20,120 e5e5e5 F1AA0E}
NAME${alignr}PID         CPU%        MEM%
${top name 1}${alignr}${top pid 1}       ${top cpu 1}          ${top mem 1}   
${top name 2}${alignr}${top pid 2}       ${top cpu 2}          ${top mem 2}   
${top name 3}${alignr}${top pid 3}       ${top cpu 3}          ${top mem 3}   
${top name 4}${alignr}${top pid 4}       ${top cpu 4}          ${top mem 4}   

${color orange}MEMORY / DISK $color
Total: ${color}${memmax} ${alignr} Free: ${color}${memfree}
RAM: $memperc% ${alignr}Swap: $swapperc% 
${memgraph 20,120 e5e5e5 F1AA0E} ${alignr} ${swapbar 20,120 }
root: ${fs_used_perc /}% ${fs_bar 6 /}$color
home: ${fs_used_perc /home/tmo}% ${fs_bar 6 /home/tmo}$color

${color orange}WIFI (${addr wlan0}) $color
${wireless_essid wlan0} ${wireless_link_bar 6 wlan0}
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 20,120 e5e5e5 F1AA0E} ${alignr}${upspeedgraph wlan0
20,120 e5e5e5 F1AA0E}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING $color
${font arial:size=7}${execi 30 tail -n 10 /var/log/messages | fold -w45}
```

I'd like to thank the original coder who put this together...looks great!

---

### Post by koleoptero on 2009-11-11
change:
minimum_size 100 800
maximum_size 100 800

and see what happens.

---

### Post by PeteyPete on 2009-11-11
> **koleoptero said:**
> change:
minimum_size 100 800
maximum_size 100 800

and see what happens.


no dice....anything else i can try?

---

### Post by PeteyPete on 2009-11-12
Anyone?

---

### Post by cariboo on 2009-11-12
Dumb question, did you log off and then back on again?

This thread really doesn't belong here, moved to Desktop Environments

---

### Post by PeteyPete on 2009-11-12
> **cariboo907 said:**
> Dumb question, did you log off and then back on again?

This thread really doesn't belong here, moved to Desktop Environments

Sorry for the wrong placement......I have tried logging on/off

---

### Post by stinkeye on 2009-11-12
Add this to your conky above "TEXT"
```
maximum_width 260
```
and adjust to whatever you like.

If you don't specify a maximum_width, the width of your conky will be
set to whatever line is drawing the widest.
The width of your conky is being set by the graphs or bars where you have set a specific size
eg```
${loadgraph 20,[COLOR="Red"]250[/COLOR] e5e5e5 F1AA0E}
${cpugraph 1 20,[COLOR="Red"]120[/COLOR] e5e5e5 F1AA0E}

```
If you want your conky to be narrower than 260 you will probably have to reduce the [COLOR="Red"]width[/COLOR] of your bars as well.
If you don't set a width for your bars it will draw to the width of your conky.
But if you have 2 bars on the one line you need to specify a width
otherwise they will draw over the top of each other.
In terminal see```
man conky
```
for variables and options.

Try this one adjusted for a width of 220.
```
# UBUNTU-CONKY
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 200 800
maximum_width 220

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

text_buffer_size 1024

# stuff after &#8216;TEXT&#8217; will be formatted on screen

TEXT
$color${font arial:size=9}
$nodename@$sysname $kernel on $machine${font arial:size=8}
Battery ${battery_bar 6 BAT0}

${color orange}CPU $color
${freq}MHz${alignr}Load: ${loadavg}
${alignr}${loadgraph 20,220 e5e5e5 F1AA0E}
CPU Total:${color} ${cpu cpu0}% ${color}${alignr}Temp:${color} ${acpitemp}
${alignr}${cpugraph 0 20,220 e5e5e5 F1AA0E}
Core one: ${color}${cpu cpu1}% ${alignr} Core two: ${color}${cpu cpu2}%
${cpugraph 1 20,100 e5e5e5 F1AA0E}${alignr}${cpugraph 2 20,100 e5e5e5 F1AA0E}
NAME${alignr}CPU%        MEM%
${top name 1}${alignr}${top cpu 1}          ${top mem 1}   
${top name 2}${alignr}${top cpu 2}          ${top mem 2}   
${top name 3}${alignr}${top cpu 3}          ${top mem 3}   
${top name 4}${alignr}${top cpu 4}          ${top mem 4}   

${color orange}MEMORY / DISK $color
Total: ${color}${memmax} ${alignr} Free: ${color}${memfree}
RAM: $memperc% ${alignr}Swap: $swapperc% 
${memgraph 20,100 e5e5e5 F1AA0E}${alignr}${swapbar 20,100}
root: ${fs_used_perc /}% ${fs_bar 6 /}$color
home: ${fs_used_perc /home/tmo}% ${fs_bar 6 /home/tmo}$color

${color orange}WIFI (${addr wlan0}) $color
${wireless_essid wlan0}${wireless_link_bar 6 wlan0}
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 20,100 e5e5e5 F1AA0E} ${alignr}${upspeedgraph wlan0
20,100 e5e5e5 F1AA0E}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING $color
${font arial:size=7}${execi 30 tail -n 10 /var/log/messages | fold -w45}
```

Also this is the best thread for all your conky questions
[_[COLOR="DarkRed"]Post your .conkyrc files w/ screenshots[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=281865&page=1044")

---

