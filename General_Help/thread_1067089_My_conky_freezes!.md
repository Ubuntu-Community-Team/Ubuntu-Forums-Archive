---
title: "My conky freezes!"
date: 2009-02-11
forum: General Help
---

### Post by matt.cohenprice on 2009-02-11
Hi, fellow conky fans.

I can't figure out what's going on, but my installation of the conky system monitor freezes pretty regularly. I've been playing with it pretty recently, trying to get [conkyweather]("http://ubuntuforums.org/showthread.php?t=869328") installed, failing, and deciding it wasn't worth my time, as well as using a script to monitor my banshee and one to check my gmail. It's pretty lightweight - so I'm not sure what is causing the freeze. 

Here's my conkyrc file:

```
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
maximum_width 200
minimum_size 200
color1 FF9966
color2 BADCDD
color3 C2E078
color4 ffffff
color5 F8DF58



TEXT
${color1}${font OpenLogos:size=38}t${font OpenLogos:size=80}${voffset -25}v
${font}${voffset -140}            ${nodename}:${user_names}
${color2}${if_running banshee-1}
${font Radio Space:size=14}${alignc}Banshee${font}
${alignc}${execi 5 ~/.scripts/banshee.sh title}
${alignc}${execi 5 ~/.scripts/banshee.sh artist}
${alignc}${execi 5 ~/.scripts/banshee.sh album}
${execibar 1 ~/.scripts/banshee.sh progress}
${else}
${font Radio Space:size=14}${alignc}Banshee${font}

${alignc}not running


${endif}
${color3}${font Radio Space:size=14}${alignc}WiFi${font}
${alignc}SSID: ${wireless_essid eth1}
 ${font Stylebats:size=16}N${font}  tx: ${wireless_bitrate eth1}  % ${wireless_link_bar eth1}
${voffset 3} ${font PizzaDude Bullets:size=16}v${font}  up: ${upspeed eth1} Kb/s (${totalup eth1})
${voffset 3} ${font PizzaDude Bullets:size=16}r${font}  down: ${downspeed eth1} Kb/s (${totaldown eth1})
${color4}
${voffset 5} ${font StyleBats:size=16}Q${font}  CPU: ${cpu cpu0}% ${cpubar cpu0}
${voffset 5}${alignr 8}${top name 1} ${top cpu 1} ${top mem 1}
${alignr 8}${top name 2} ${top cpu 2} ${top mem 2}
${alignr 8}${top name 3} ${top cpu 3} ${top mem 3}
${voffset 5} ${font PizzaDude Bullets:size=16}J${font}${voffset -7}  ram:	${memperc}% ${membar}
${voffset -3}        swap:	${swapperc}% ${swapbar}
${color5}
${voffset 5} ${font StyleBats:size=16}A${font}  /home: ${fs_bar /home}
${voffset -2}${alignr 3}Free: ${fs_free /home}
${voffset -3} ${font StyleBats:size=16}A${font}  /root:  ${fs_bar /}
${voffset -2}${alignr 3}Free: ${fs_free /}
${color2}
 ${font StyleBats:size=16}8${font}  Battery: ${battery_percent BAT1}% ${battery_bar BAT1}
${voffset 5} ${font StyleBats:size=18}P${font}  Uptime:  ${uptime_short}

${color1} ${font FreeSans:size=16}@${font}${execpi 300 python ~/.scripts/gmail_parser.py matt.cohenprice tinker3toes 0}

${font Radio Space:size=18}${alignc}${time %A}
${voffset -3}${font Radio Space:size=14}${alignc}${time %d.%m.%Y}

```

I tried launching conky ten seconds after system startup by creating a sleep script and adding it to my sessions --> startup programs. It works just fine....just doesn't fix the problem.

```

#!/bin/bash
sleep 10 && conky

```

Can anyone help me out? 

Note: It doesn't freeze up any other part of the system...it just stops refreshing. Battery, Banshee feed, Wifi details, etc... just pauses and I have to run 
```

killall -9 conky

```
from terminal and then restart it if it gets stuck.

Screenshot attached. 
Thanks!

---

### Post by amangu on 2009-02-11
I'm experiencing the same problem....I think my script is pretty light as well....

Conkyrc file:

```

use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
maximum_width 500
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color ffffff
use_spacer none
no_buffers yes
uppercase no
color1 ffffff


TEXT 
 $font${color ffffff}
 $sysname $kernel $alignr $machine
 Intel Pentium M $alignr${freq_g cpu0}Ghz
 File System $alignr${fs_type}

${color ffffff}${font weather:size=80}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -20}  ${execi 1200 ~/scripts/pogodynka.sh}
    
   
${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth1} Kb/s 
${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth1} Kb/s 

${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth1}
${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth1}
   
${font PizzaDude Bullets:size=16}Z${font}   Signal: ${wireless_link_qual eth1}% ${alignr}${wireless_link_bar 8,60 eth1}
   
${font PizzaDude Bullets:size=16}a${font}   Local Ip: ${alignr}${addr eth1}
  
${color ffffff}${font PizzaDude Bullets:size=16}z${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

${color ffffff}${font PizzaDude Bullets:size=16}A${font}  Battery: ${battery_percent}% ${battery_bar}

${color ffffff}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py top secret 3}

${color ffffff}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


  ${font Radio Space:size=14}${time %A %d %Y}
${font Radio Space:size=50}${time %H:%M}
```



I'm just curious, it's been buggin me for a while, I'm just not that savvy in Ubuntu as of yet as to correct it..

---

### Post by civillian on 2009-02-12
I've been having a smiliar problem with my conky, so I'm running it from the terminal to see what errors get thrown up, currently just one about a possibly dodgy "if" statement I have...

for reference, my conkyrc is as follows

```
background yes
use_xft yes
xftfont HandelGotD:size=8
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
alignment top_right
gap_x 10
gap_y 10
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes

TEXT

${voffset -7}$hr $color
john-desktop
Linux 2.6.27-10-generic
Athlon(tm) 64 X2 Dual Core Processor 5000+
${voffset -7}$hr $color

${voffset -7}$hr $color
Banshee
${voffset -7}$hr $color

${if_running banshee-1}
${color1}${alignc}Banshee Now Playing${color white}
${alignc}${execi 5 /home/john/.conky/scripts/banshee.sh artist}
${alignc}${execi 5 /home/john/.conky/scripts/banshee.sh title}
${color1}${execibar 1 /home/john/.conky/scripts/banshee.sh progress}$color
$endif
${if_running banshee}
${color1}${alignc}Banshee Now Playing${color white}
${alignc}${execi 5 /home/john/.conky/scripts/banshee.sh artist}
${alignc}${execi 5 /home/john/.conky/scripts/banshee.sh title}
${color1}${execibar 1 /home/john/.conky/scripts/banshee.sh progress}$color
$endif


${voffset -7}$hr $color
Processors
${voffset -7}$hr $color

CPU1 ${cpu cpu1}% ${cpubar cpu1}
CPU2 ${cpu cpu2}% ${cpubar cpu2}

${voffset -7}$hr $color
Memory
${voffset -7}$hr $color

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

${voffset -7}$hr $color
Disk Space
${voffset -7}$hr $color

/home $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /home}
${if_mounted /media/disk} /disk $color${fs_used /media/disk/}/${fs_size /media/disk/} 
${fs_bar /media/disk/}$endif

${voffset -7}$hr $color
Top Processes
${voffset -7}$hr $color

CPU $alignr CPU% MEM%

${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 2}${top mem 3}

MEM $alignr CPU% MEM%

${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${voffset -7}$hr $color
Network
${voffset -7}$hr $color

IP on eth1 $alignr ${addr eth0}

Down $alignr ${downspeed eth0} kb/s
${downspeedgraph eth0}
Up $alignr ${upspeed eth0} kb/s
${upspeedgraph eth0 16,200}

Downloaded: $alignr ${totaldown eth0}
Uploaded: $alignr ${totalup eth0}
```

its a bit scruffy in places (for example the banshee/banshee-1 bit) but that hasn't been the problem, only the one that comes up form this
> ${if_mounted /media/disk} /disk $color${fs_used /media/disk/}/${fs_size /media/disk/} 
${fs_bar /media/disk/}$endif

---

### Post by illmatic on 2009-03-18
Hm my conky freezes too.
It runs for 10 seconds and then it freezes for 40-50 seconds.

If I run conky in the terminal i get following message:

(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)

If I logg in with my account as root, I get conky in a window but it works o.O
Anyone any idea?

---

### Post by Pépou on 2009-06-18
Same problem for me ! Please help !

---

### Post by Pépou on 2009-06-19
I just found a solution : install the last version of conky here : [http://www.getdeb.net/app/Conky]("http://www.getdeb.net/app/Conky")

Bye !

Edit : I've spoken to quickly ! Conky is still freezing !

Here is my .conkyrc file :

```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes    # On dit à Conky de ne pas se mettre sur le bureau ais dans une fenêtre propre
own_window_type override  # type de fenêtre "maison" (le type desktop convient si on n'a pas d'ombre)
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager # définition du type 
own_window_transparent yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 5

maximum_width 200

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color black
# default_shade_color black
# default_outline_color black
own_window_colour black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
SYSTEME ${hr 2}
${font OpenLogos:size=16}u${font}  Kernel :  ${alignr}${kernel}
${font StyleBats:size=16}A${font}  Core 1 : ${cpu cpu1}% ${alignr}${cpubar 8,60 cpu1}
${font StyleBats:size=16}A${font}  Core 2 : ${cpu cpu2}% ${alignr}${cpubar 8,60 cpu2}
${font StyleBats:size=16}g${font}  RAM :  $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}  SWAP : $swapperc% ${alignr}${swapbar 8,60}
${font Webdings:size=16}~${font} Batterie: ${alignr}${battery_bar 8,60 BAT0}
${font StyleBats:size=16}q${font}  Uptime : ${alignr}${uptime}

STOCKAGE ${hr 2}
${font PizzaDude Bullets:size=14}g${font}   Root :
${fs_used /}/${fs_size /} $alignr${fs_bar 8,60 /}
${font PizzaDude Bullets:size=14}g${font}   Home :
${fs_used /home}/${fs_size /home} $alignr${fs_bar 8,60 /home}

RESEAUX ${hr 2}
${if_existing /proc/net/route wlan0}    
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up : ${upspeed wlan0} kb/s $alignr${upspeedgraph wlan0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down : ${downspeed wlan0} kb/s $alignr${downspeedgraph wlan0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal : ${wireless_link_qual wlan0}% $alignr${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   IP locale : $alignr${addr wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   IP publique : $alignr${execi 1 ~/.scripts/ip.sh}
${endif}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up : ${upspeed eth0} kb/s $alignr${upspeedgraph eth0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down : ${downspeed eth0} kb/s $alignr${downspeedgraph eth0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   IP locale : $alignr${addr eth0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   IP publique : $alignr${execi 600 ~/.scripts/ip.sh}
${endif}

METEO  - ${execi 120 ~/.conky/meteo.sh FRXX0073} ${execi 120 ~/.conky/meteo2.sh "Nice"} ${hr 2}

Aujourd'hui : ${execi 120 ~/.conky/meteo2.sh "Température aujourd'hui"}  ${font weather:size=40}${voffset -18}${execi 120 ~/.conky/meteo2.sh "Conditions aujourd'hui"}${font}${voffset -11}
Vent : ${execi 120 ~/.conky/meteo2.sh "Vent aujourd'hui"}
Lever du soleil : ${execi 120 ~/.conky/meteo2.sh "Lever du soleil"}
Coucher du soleil : ${execi 120 ~/.conky/meteo2.sh "Coucher du soleil"}

Demain : ${execi 120 ~/.conky/meteo2.sh "Température demain"}  ${font weather:size=32}${voffset -10}${execi 120 ~/.conky/meteo2.sh "Conditions demain"}${font}
```

---

### Post by jonicunha on 2009-07-31
same here. my conkyrc

[HTML]# Use Xft?
use_xft yes
xftfont Calibri:bold:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
maximum_width 180

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_inner_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color white
#default_outline_color black
own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 20
gap_y 70

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
SISTEMA ${hr 2}
${voffset 2}${font OpenLogos:size=12}u${font}  Kernel:  ${alignr}${kernel}
${font StyleBats:size=12}A${font}  CPU: ${cpu cpu}% ${alignr}${cpubar cpu 8,60}
${font StyleBats:size=12}g${font}  RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=12}j${font}  SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font Webdings:size=12}~${font} Bateria: ${battery_percent BAT1}% ${alignr}${battery_bar 8,60 BAT1}
${font StyleBats:size=12}q${font}  Ligado: ${alignr}${uptime}

DATA ${hr 2}
${alignc 35}${font Arial Black:size=22}${time %H:%M}${font}
${alignc}${time %A %d %Y}

HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=10}7${font}   ${voffset -5}Root:
${voffset 4}${fs_free /}/${fs_size /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=10}7${font}   ${voffset -5}Home:
${voffset 4}${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}

REDE ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PizzaDude Bullets:size=10}O${font}   Up: ${upspeed wlan0} ${alignr}${upspeedgraph wlan0 8,60}
${voffset 4}${font PizzaDude Bullets:size=10}U${font}   Down: ${downspeed wlan0} ${alignr}${downspeedgraph wlan0 8,60}
${voffset 4}${font PizzaDude Bullets:size=10}N${font}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDude Bullets:size=10}T${font}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDude Bullets:size=10}Z${font}   Sinal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=10}a${font}   Ip Local: ${alignr}${addr wlan0}
${voffset 4}${font PizzaDude Bullets:size=10}b${font}   Ip Externo: ${alignr}${execi 1 ~/.scripts/ip.sh}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=10}O${font}   Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60}
${voffset 4}${font PizzaDude Bullets:size=10}U${font}   Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60}
${voffset 4}${font PizzaDude Bullets:size=10}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=10}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=10}a${font}   Ip Local: ${alignr}${addr eth0}
${voffset 4}${font PizzaDude Bullets:size=10}b${font}   Ip Externo: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif} ${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=10}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60}
${voffset 4}${font PizzaDude Bullets:size=10}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60}
${voffset 4}${font PizzaDude Bullets:size=10}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=10}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=10}a${font}   Ip Local: ${alignr}${addr eth1}
${voffset 4}${font PizzaDude Bullets:size=10}b${font}   Ip Externo: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif} ${else}
${font PizzaDude Bullets:size=10}4${font}   Rede indisponível
${endif}
${endif}
TEMPO ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=POXX0037 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=24}${execi 600 conkyForecast --location=POXX0037 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=POXX0037 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=POXX0037 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=POXX0037 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=POXX0037 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=POXX0037 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=POXX0037 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=POXX0037 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=POXX0037 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=POXX0037 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=POXX0037 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=POXX0037 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=POXX0037 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=POXX0037 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${else}${if_existing /proc/net/route eth0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=POXX0037 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=24}${execi 600 conkyForecast --location=POXX0037 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=POXX0037 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=POXX0037 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=POXX0037 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=POXX0037 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=POXX0037 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=POXX0037 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=POXX0037 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=POXX0037 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=POXX0037 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=POXX0037 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=POXX0037 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=POXX0037 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=POXX0037 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${endif} ${else}${if_existing /proc/net/route eth1}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=POXX0037 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=24}${execi 600 conkyForecast --location=POXX0037 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=POXX0037 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=POXX0037 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=POXX0037 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=POXX0037 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=POXX0037 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=POXX0037 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=POXX0037 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=POXX0037 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=POXX0037 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=POXX0037 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=POXX0037 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=POXX0037 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=POXX0037 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${endif} ${else}
${font PizzaDude Bullets:size=14}4${font}   Tempo indisponível
${endif}
${endif}
MAIL ${hr 2}
${font Martin Vogel's Symbols:size=16}B${font} Gmail: ${execi 1800 conkyEmail --servertype=POP --servername=pop.gmail.com --port=995 --ssl --username=xxx@gmail.com --password=xxxxxx} Novo(s) mail(s)
${font Martin Vogel's Symbols:size=16}B${font} Netvisão: ${execi 1800 conkyEmail --servertype=POP --servername=pop.netvisao.pt --username=xxx --password=xxxxxx} Novo(s) mail(s)

MPD ${hr 2}
${mpd_vol}% VOL
${alignc}$mpd_status
${alignc}$mpd_artist
${alignc}$mpd_title
$mpd_elapsed ${mpd_bar 8,140} ${alignr}$mpd_length[/HTML]

---

### Post by KlinerDraken on 2009-08-02
Mine freezes too :confused:

I have the same config on two computers, one desktop and one laptop, and it started freezing at the same time. So I think it was an update I installed?

---

### Post by ukblacknight on 2009-08-11
I'm having the same problem.  It didn't used to do this, kinda started suddenly.  It updates maybe every 20 or 30 minutes for a second, where as it used to update every second.  My friend is also having this same problem.

---

### Post by pinguy on 2009-08-14
Same here, tried installing the new version but still having the same problem.

```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 200

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color white
own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}u${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu0}% ${alignr}${cpubar cpu0 8,60}
${font StyleBats:size=16}A${font}   CPU2: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font Webdings:size=16}~${font}  Battery: ${battery_percent BAT0}% ${alignr}${battery_bar 8,60 BAT0}
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 35}${font Arial Black:size=26}${time %H:%M}${font}
${alignc}${time %A %d %Y}

HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Root:
${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:
${voffset 4}${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}

NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}${if_existing /proc/net/route ppp0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 F57900 FCAF3E}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}
WEATHER ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=UKXX0113 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=UKXX0113 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=UKXX0113 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${voffset 0}Wind: ${alignr}${execi 600 conkyForecast --location=UKXX0113 --datatype=WS}
${voffset 0}Humidity: ${alignr}${execi 600 conkyForecast --location=UKXX0113 --datatype=HM}
${else}${if_existing /proc/net/route eth0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=UKXX0113 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=UKXX0113 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=UKXX0113 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${voffset 0}Wind: ${alignr}${execi 600 conkyForecast --location=UKXX0113 --datatype=WS}
${voffset 0}Humidity: ${alignr}${execi 600 conkyForecast --location=UKXX0113 --datatype=HM}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=UKXX0113 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=UKXX0113 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=UKXX0113 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${voffset 0}Wind: ${alignr}${execi 600 conkyForecast --location=UKXX0113 --datatype=WS}
${voffset 0}Humidity: ${alignr}${execi 600 conkyForecast --location=UKXX0113 --datatype=HM}
${endif}${else}${if_existing /proc/net/route ppp0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=UKXX0113 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=UKXX0113 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=UKXX0113 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=UKXX0113 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=UKXX0113 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=UKXX0113 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${voffset 0}Wind: ${alignr}${execi 600 conkyForecast --location=UKXX0113 --datatype=WS}
${voffset 0}Humidity: ${alignr}${execi 600 conkyForecast --location=UKXX0113 --datatype=HM}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Weather Unavailable
${endif}

EMAIL ${hr 2}

${voffset -8}${font Martin Vogel's Symbols:size=19}B${font}  Gmail: ${alignr}${font DejaVu Sans:style=Bold:size=8}${execi 600 conkyEmail --servertype=IMAP --servername=imap.googlemail.com --username=******** --password=********** --ssl}${font} New email(s)


```

---

### Post by maximalistic on 2009-08-14
I have the same problem! it might have happen after a conky update but im not sure! 
```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 2

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 200

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color white
own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}u${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font}   CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 35}${font Arial Black:size=26}${time %H:%M}${font}
${alignc}${time %A %d %Y}

HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home: ${alignr}${diskiograph /dev/sdc 8,60 789E2D A7CC5C}${alignr}
${voffset 4}${fs_free /home} / ${fs_size /home} ${alignr}${fs_bar 8,60 /home}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Misc1: ${alignr}${diskiograph /dev/sdb1 8,60 789E2D A7CC5C}${alignr}
${voffset 4}${fs_free /media/misc1} / ${fs_size /media/misc1} ${alignr}${fs_bar 8,60 /media/misc1}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Music: ${alignr}${diskiograph /dev/sdb2 8,60 789E2D A7CC5C}${alignr}
${voffset 4}${fs_free /media/music} / ${fs_size /media/music} ${alignr}${fs_bar 8,60 /media/music}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Gigant: ${alignr}${diskiograph /dev/sda 8,60 789E2D A7CC5C}${alignr}
${voffset 4}${fs_free /media/gigant} / ${fs_size /media/gigant} ${alignr}${fs_bar 8,60 /media/gigant}



NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth0}/s ${alignr}${upspeedgraph eth0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth0}/s ${alignr}${downspeedgraph eth0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
${voffset 4}${font PizzaDude Bullets:size=14}b${font}   Public Ip: ${alignr}${execi 1 ~/.scripts/ip.sh}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}
WEATHER ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=SWXX0015 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=SWXX0015 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=SWXX0015 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${else}${if_existing /proc/net/route eth0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=SWXX0015 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=SWXX0015 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=SWXX0015 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=SWXX0015 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=SWXX0015 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=SWXX0015 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Weather Unavailable
${endif}
```

---

### Post by mastatux on 2009-08-14
I think I figured it out.

Edit the ip.sh file located in ~/.scripts/.

```

nano ~/.scripts/ip.sh
```

and replace the text with

```
#!/bin/bash
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
```

Don't forget to save!

Tell me how it goes for you guys.

Cheers!:)

-If that doesn't work I would just tell conky not to call it anymore.

---

### Post by maximalistic on 2009-08-14
didnt work for me :(

---

### Post by mastatux on 2009-08-14
Maximalist try this conky config. 

```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 200

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color white
own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}u${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font}   CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 35}${font Arial Black:size=26}${time %H:%M}${font}
${alignc}${time %A %d %Y}

HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home: ${alignr}${diskiograph /dev/sdc 8,60 789E2D A7CC5C}${alignr}
${voffset 4}${fs_free /home} / ${fs_size /home} ${alignr}${fs_bar 8,60 /home}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Misc1: ${alignr}${diskiograph /dev/sdb1 8,60 789E2D A7CC5C}${alignr}
${voffset 4}${fs_free /media/misc1} / ${fs_size /media/misc1} ${alignr}${fs_bar 8,60 /media/misc1}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Music: ${alignr}${diskiograph /dev/sdb2 8,60 789E2D A7CC5C}${alignr}
${voffset 4}${fs_free /media/music} / ${fs_size /media/music} ${alignr}${fs_bar 8,60 /media/music}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Gigant: ${alignr}${diskiograph /dev/sda 8,60 789E2D A7CC5C}${alignr}
${voffset 4}${fs_free /media/gigant} / ${fs_size /media/gigant} ${alignr}${fs_bar 8,60 /media/gigant}



NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr wlan0}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth0}/s ${alignr}${upspeedgraph eth0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth0}/s ${alignr}${downspeedgraph eth0 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 789E2D A7CC5C}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}
WEATHER ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=SWXX0015 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=SWXX0015 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=SWXX0015 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${else}${if_existing /proc/net/route eth0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=SWXX0015 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=SWXX0015 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=SWXX0015 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=SWXX0015 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=SWXX0015 --datatype=HT}${font}

${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=SWXX0015 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=SWXX0015 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=SWXX0015 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SWXX0015 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Weather Unavailable
${endif}

maximalistic is online now Report Post   	Reply With Quote Multi-Quote This Message Quick reply to this message
maximalistic
View Public Profile
Send a private message to maximalistic
Find More Posts by maximalistic
Add maximalistic to Your Contacts

```

I'm double checking you removed where it calls ip.sh.
When you run this your Public IP info will be missing. 
If this fixes it though, I'll help you get that stuff back.

I also noticed your update interval was 2. I changed that as well. Usually if you have something like uptime you want conky to be updated every second. ;)

Your config ran fine on mine. I'll take another look at it if this new config doesn't work for you.

---

### Post by KlinerDraken on 2009-08-14
> **mastatux said:**
> I think I figured it out.

Edit the ip.sh file located in ~/.scripts/.

```

nano ~/.scripts/ip.sh
```

and replace the text with

```
#!/bin/bash
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
```

Don't forget to save!

Tell me how it goes for you guys.

Cheers!:)

-If that doesn't work I would just tell conky not to call it anymore.

Changing the ip.sh did not fix my issue, however removing any call to that script from the .conkyrc file did fix it.

Thanks for your tip!

---

### Post by mastatux on 2009-08-14
Okay, it seems like the ip.sh I provided wasn't going over too well.
However, it looks like it is the ip.sh file conky calls that causes the freezes.

You can replace where it calls ip.sh in you conky config file with something like this:

```

Public IP: (${execi 3600 wget -O - http://whatismyip.org/ | tail})
```

Or I suggest removing it.

See how that works.

:)

---

### Post by maximalistic on 2009-08-15
> **mastatux said:**
> Okay, it seems like the ip.sh I provided wasn't going over too well.
However, it looks like it is the ip.sh file conky calls that causes the freezes.

You can replace where it calls ip.sh in you conky config file with something like this:

```

Public IP: (${execi 3600 wget -O - http://whatismyip.org/ | tail})
```

Or I suggest removing it.

See how that works.

:)

that fixed it for me! thanks alot!

---

### Post by jjgomera on 2009-08-15
I think the problem is the double buffer, in conkyrc maybe is active, but it must be active in xorg.conf too, so try edit /etc/X11/xorg.conf and add this section:

```
Section "Module"
	Load	"dbe"
EndSection
```

---

### Post by pinguy on 2009-08-15
> **mastatux said:**
> Okay, it seems like the ip.sh I provided wasn't going over too well.
However, it looks like it is the ip.sh file conky calls that causes the freezes.

You can replace where it calls ip.sh in you conky config file with something like this:

```

Public IP: (${execi 3600 wget -O - http://whatismyip.org/ | tail})
```

Or I suggest removing it.

See how that works.

:)

Thanks that did the trick.

---

### Post by maximalistic on 2009-08-20
ok whatismyip.org seems to be down and that makes my conky freeze again, isnt there away to get like "Public ip: unknown" or something instead of the whole config freezing?

---

### Post by zakoo2 on 2011-11-11
okay, this thread might be two years old, but i feel the need to update it a lil bit, since i had the same problem. i dont have any reference to external ip in my conkyrc, so i figured the ip.sh is not a solution for me, so i started trying things, and they seem to work. three things i changed in my conkyrc, dunno which helped, but here they are:
no_buffers - default is 'yes', changed it to 'no'
cpu_avg_samples - default is '2', changed it to '1'
net_avg_samples - default is '2', changed is to '1'
dont know exactly what these things do, but my conky is working properly, doesnt freeze, and the readings are accurate. hope it helps you guys!

---

