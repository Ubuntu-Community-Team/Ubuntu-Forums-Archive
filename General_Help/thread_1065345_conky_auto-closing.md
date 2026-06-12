---
title: "conky auto-closing?"
date: 2009-02-09
forum: General Help
---

### Post by sidyom on 2009-02-09
hey yall

been having some problems with my conky lately. i have added conky to start on boot, and have a little bash script to run to delay the start by 10 seconds so that x will manage the window properly.

however, now when i boot up, my conky appears on my desktop like normal, but after a few seconds it closes.

when i try to rerun it in the terminal, i get this:

```
x@x:~$ conky
Conky: $else: no matching $if_*
Conky: desktop window (1c0002e) is subwindow of root window (85)
Conky: window type - override
Conky: drawing to created window (0x3400001)
Conky: drawing to double buffer
Conky: you don't need that many fonts, sorry.
x@x:~$ 

```

i've googled around but the answers are in other languages...

here's my .conkyrc

```

#  Here we go...
#  Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
#
#  Update interval in seconds
update_interval 1
#
#  This is the number of times Conky will update before quitting.
#  Set to zero to run forever.
total_run_times 0
#
own_window yes
own_window_transparent yes
own_window_type override
#own_window_type desktop
#own_window_type normal #use this if you want a nice shadow to appear around conky
#
#  If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#
#  Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
#
#  Minimum size of text area
minimum_size 180 0
# maximum_width 200
#
#  Draw shades?
draw_shades no
#
#  Draw outlines?
draw_outline no
#
#  Draw borders around text
draw_borders no
#
#  Stippled borders?
stippled_borders 0
#
#  border margins
border_margin 5
#
#  border width
border_width 1
#
#  Default colors and also border colors
default_color grey
# default_shade_color black
# default_outline_color grey
own_window_colour grey
#
#  Text alignment, other possible values are commented
# alignment top_left
alignment top_right
# alignment bottom_left
# alignment bottom_right
#
#  Gap between borders of screen and text
#  same thing as passing -x at command line
gap_x 12
gap_y 12
#
#  Subtract file system buffers from used memory?
no_buffers yes
#
#  set to yes if you want all text to be in uppercase
uppercase no
#
#  number of cpu samples to average
#  set to 1 to disable averaging
cpu_avg_samples 2
#
#  number of net samples to average
#  set to 1 to disable averaging
net_avg_samples 2
#
#  Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes
#
#  Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none
#
TEXT
SYSTEM ${hr 2}
${alignc 19}${font Arial Black:size=16}${nodename}${font}
${font OpenLogos:size=16}u${font}   kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   cpu: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}g${font}   ram: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   swap: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}q${font}   uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 19}${font Arial Black:size=18}${time %l:%M}${font}
${voffset 2}${alignc}${time %A, %d %B %Y}

WEATHER ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -8}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=USTX0225 --datatype=WF}${font}
${voffset -52}${font Weather:size=40}y${font}   ${voffset -38}${font Trebuchet MS:size=26}${execi 600 conkyForecast --location=USTX0225 --datatype=HT --imperial}${font}

${voffset 0}current conditions: ${alignr}${execi 600 conkyForecast --location=USTX0224 --datatype=CC}
${voffset 0}humidity: ${alignr}${execi 600 conkyForecast --location=USTX0225 --datatype=HM}
${voffset 0}${font}wind speed: ${alignr}${execi 600 conkyForecast --location=USTX0225 --hideunits --datatype=WS --imperial} mi/h ${execi 600 conkyForecast --location=USTX0225 --hideunits --datatype=WD}
${voffset 0}${font}wind gusts: ${alignr}${execi 600 conkyForecast --location=USTX0225 --hideunits --datatype=WG --imperial} mi/h
${voffset 0}daylight: ${alignr}${execi 600 conkyForecast --location=USTX0225 --datatype=SR} - ${execi 600 conkyForecast --location=USTX0225 --datatype=SS}

${voffset 0}forecast: ${alignr}low:${execi 600 conkyForecast --location=USTX0225 --datatype=LT --datatype=DW --startday=1 --endday=3 --imperial}

${else}${if_existing /proc/net/route wlan0}
${voffset -8}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=USTX0225 --datatype=WF}${font}
${voffset -52}${font Weather:size=40}y${font}   ${voffset -38}${font Trebuchet MS:size=26}${execi 600 conkyForecast --location=USTX0225 --datatype=HT --imperial}${font}

${voffset 0}humidity: ${alignr}${execi 600 conkyForecast --location=USTX0225 --datatype=HM}
${voffset 0}${font}wind speed:USTX0225 --hideunits --datatype=WD}
${voffset 0}${font}wind gusts: ${alignr}${execi 600 conkyForecast --location=USTX0225 --datatype=WG}
${voffset 0}daylight: ${alignr}${execi 600 conkyForecast --location=USTX0225 --datatype=SR} - ${execi 600 conkyForecast --location=USTX0225 --datatype=SS}

${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Weather Unavailable
$endif}

${voffset -10}HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}root:
${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}

NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 BEBEBE BEBEBE}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 BEBEBE BEBEBE}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}Y${font}   network: ${alignr}${wireless_essid wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}?${font}   local ip: ${alignr}${addr wlan0}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}    Network Unavailable
```

thanks in advance!

---

### Post by sidyom on 2009-02-09
EDIT: figured it out, there was a problem with my endif and else statements...

---

