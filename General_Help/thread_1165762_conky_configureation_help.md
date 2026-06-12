---
title: "conky configureation help"
date: 2009-05-21
forum: General Help
---

### Post by c/Kr3t on 2009-05-21
hello, i just started using conky and i'm starting to get the hang of it.

i have a problem with the window border. it looks as if it's hovering ever so slightly above my desktop and it leaves an annoying shade under it. i'll include a picture, this is my config. I've looked everywhere that has the tag conky but i can't find anything at all that describes my condition.

If anyone could tell me what to add or change to get rid of the shade that would be amazing. thank you


```

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 0.9

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 1

# border margins
border_margin 8

# border width
border_width 0

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

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

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT


${offset 240}${color slate grey}$nodename
${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$sysname $kernel $machine
${offset 240}${font StyleBats:size=16}${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
${offset 240}${font StyleBats:size=16}${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}
${offset 240}${font StyleBats:size=16}${font}  CPU2: ${cpu cpu2}% ${cpubar cpu2}
${offset 240}${font StyleBats:size=16}${font}  CPU3: ${cpu cpu3}% ${cpubar cpu3}
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes
${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}
${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}
${offset 240}${color slate grey}RAM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}
${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}share:  ${color }${fs_free /media/share}/${fs_size /media/share}
${offset 240}${fs_bar 3,100 /media/share}
${offset 240}${color slate grey}Networking:${color #00ee00} eth0 - $color ${addr eth0}
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color slate grey}Port Statistics:
${offset 240}${color red} ${tcp_portmon 1 65535 count} $color total connections
${offset 240}${color red} ${tcp_portmon 1 1024 count} $color btw ${color red}1-1024
${offset 240}${color green} ${tcp_portmon 80 80 count} $color on ${color red}80
${offset 240}${color green} ${tcp_portmon 20 23 count} $color on ${color red}20-23
${offset 240}${color green} ${tcp_portmon 443 443 count} $color on ${color red}443

```


[IMG]http://i43.tinypic.com/wbs1eq.jpg[/IMG]

---

### Post by m_duck on 2009-05-21
It's because of conky and compiz having disagreement. Either you can fiddle around with compiz settings and tell it not to shade conky windows (not sure how, I don't use compiz) or you can delay the startup of conky.

I use the second method but starting conky with a script like the following in my autostarted apps:```
#!/bin/bash
sleep 20 && conky;
```You may need to adjust the sleep time (ie time to wait before executing conky). Then you need to make the script executable so in terminal:```
chmod +x /path/to/script
```For example, a script in your home called "start_conky":```
chmod +x ~/start_conky
```Finally, add the script to autostart instead of conky (so for "Command" or whatever it is, replace conky with /home/username/start_conky.

Hope that makes sense...

EDIT: Thread [thread=1163865]here[/thread] mentioning the compiz workaround.

---

### Post by whitethorn on 2009-05-21
You might also want to change the minimun horizontal size.  So that it's doesn't extend that far left.

---

