---
title: "Conky Crashes Seemingly At Random"
date: 2011-11-21
forum: Desktop Environments
---

### Post by onethirtythreeseven on 2011-11-21
I use Conky to display various system resources, as well as to display news headlines via RSS and monitor Banshee.  It doesn't seem to crash because of the RSS or Banshee, as they seem to update just fine.  However, Conky always ends up crashing.  Sometimes within minutes of loading my config file.  Sometimes it will run fine for a few hours before crashing.  I noticed the following in /var/log/syslog, and it seems to coincide with every Conky crash.

```
Nov 21 13:54:44 lappy kernel: [ 2555.765877] conky[2646] general protection ip:7f1be71e9d13 sp:7ffff1593ba8 error:0 in ld-2.13.so[7f1be71e3000+21000]
```

Here is my Conky config:

```
#avoid flicker
double_buffer yes
background yes

#own window to run simultanious 2 or more conkys
own_window_class Conky
own_window yes
own_window_type conky
own_window_transparent 
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

#borders
draw_borders no
border_outer_margin 0

#shades
draw_shades no

#position
alignment bottom_middle
gap_y 0
gap_x 0

#behaviour
update_interval 1

#colour
default_color ffffff
color2 E04613
color3 929292

#default_shade_color 000000
own_window_colour 262729

#font
use_xft yes
xftfont PF Tempesta Five Condensed:pixelsize=8

#to prevent window from moving
use_spacer none
minimum_size 1440 55

#default bar size
default_bar_size 250 4

TEXT
${image ~/conky/background3.png -p -5,20 }
${offset 20}${voffset -9}${font PF Tempesta Five Condensed:size=6:style=bold}${color2}[ ${color}$nodename   $kernel${color2} ]${color}${font}
${offset 20}${voffset 15}load  ${color2}[ ${color}${loadavg 1} ${color2}] [ ${color}${loadavg 2} ${color2}] [ ${color}${loadavg 3} ${color2}]
${offset 20}${color}Uptime  ${color2}[ ${color}$uptime_short ${color2}]

${offset 190}${voffset -59}${color}CPU
${offset 190}${voffset 15}Core1   ${color2}[ ${color}${cpu cpu1}${color2} ]${color}
${offset 190}Core2  ${offset 1}${color2}[ ${color}${cpu cpu2}${color2} ]${color}

${offset 290}${voffset -59}Memory
${offset 290}${voffset 15}Used   ${color2}[ ${color}$mem${color2} ]${color}
${offset 290}$color3${membar 4,80} $color

${offset 430}${voffset -59}HDD
${offset 430}${voffset 15}root     ${color2}[ ${color}${fs_used /}${color2} ]${color3}
${offset 430}${fs_bar 4,80}${color}

${offset 570}${voffset -59}Network
${offset 570}${voffset 15}local ip    ${color2}[ ${color}${addr wlan0}${color2} ]${color}
${offset 570}public ip   ${color2}[ ${color}${execi 100 ~/conky/publicip.sh}${color2} ]${color}

${offset 725}${voffset -59}new york times ${color2}-${color} world headlines
${offset 725}${voffset 15}${rss http://feeds.nytimes.com/nyt/rss/World 1 item_title 0}
${offset 725}${rss http://feeds.nytimes.com/nyt/rss/World 1 item_title 1}

${offset 1100}${voffset -59}now playing
${offset 1100}${voffset 16}$color3${execibar 1 conkyBanshee --datatype=PP}$color  ${voffset -1}${exec conkyBanshee --datatype=PT}${color2}/${color}${exec conkyBanshee --datatype=LE}
${offset 1100}${exec conkyBanshee --datatype=AR} ${color2}-${color} ${exec conkyBanshee --datatype=TI}
```

I'm using Ubuntu 11.10 and Gnome 3.2.  

Any ideas as to what's going on?

---

### Post by onethirtythreeseven on 2011-11-21
bump

---

