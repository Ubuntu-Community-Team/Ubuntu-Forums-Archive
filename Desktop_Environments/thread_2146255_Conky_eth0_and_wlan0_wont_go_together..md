---
title: "Conky: eth0 and wlan0 wont go together."
date: 2013-05-17
forum: Desktop Environments
---

### Post by DragonFart on 2013-05-17
my laptop can connect to both eth0 aswellas wlan0 but when wlan0 is enabled together with eth0, the bottom half got cut out. but if wlan0 is disabled it comes back normal. anyone knows how to fix this?

thannks.

My conky script:
```

# Use Xft?
use_xft yes
xftfont Open Sans Light:size=8
xftalpha 0.8
text_buffer_size 2048
uppercase yes


# Update interval in seconds
update_interval 1


# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0


# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#own_window_argb_visual yes
#own_window_argb_value 255


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes


minimum_size 250
maximum_width 280


own_window_type normal


# Draw shades?
draw_shades yes
default_shade_color 292421
# Draw outlines?
draw_outline no


# Draw borders around text
draw_borders no


# Stippled borders?
stippled_borders 0


# border margins
border_inner_margin 5
border_outer_margin 0
draw_graph_borders no
# border width
border_width 0


# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right


# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
gap_y 10


#    Distric-Thin            fonts
#    Blue Highway
#    Raleway
#    Zekton
#    Calibri
#    Engebrechtre
#    Opeln2001
#    Open Sans Light
#    Open Sans Light


# -- Lua Load -- #
lua_load ~/.conky/.draw_bg.lua
lua_draw_hook_pre draw_bg


lua_load ~/.conky/.bargraph_small.lua
lua_draw_hook_post main_bars


imlib_cache_size 0


color1 000000 #black
color2 48FF00 #green
color3 B5A100 #yellow
color4 B3B3B3 #silver
color5 7A7A7A #darksilver
color6 00ADA7 #blue
color7 F2D03B


TEXT
${color4}${lua conky_draw_bg}${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=1098081&u=c" -o ~/.cache/weather.xml}${font Open Sans Light:size=15}${execi 300 grep "yweather:location" ~/.cache/weather.xml | grep -o "city=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}, ${execi 300 grep "yweather:location" ~/.cache/weather.xml | grep -o "country=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${font}
${color5}${font Open Sans Light:size=45}${alignr}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}°${font}
${lua conky_draw_bg}${execi 300 cp -f ~/.weathericons/$(grep "yweather:condition" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*").png ~/.cache/weather.png}${image ~/.cache/weather.png -p 0,45 -s 60x60}
${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "text=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}
${color6}${execi 300 grep "yweather:wind" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${execi 300 grep "yweather:units" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${color}
${lua conky_draw_bg}${execi 300 cp -f ~/.weathericons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | head -n1).png ~/.cache/weather-today.png}${image ~/.cache/weather-today.png -p 0,175 -s 30x30}${execi 300 cp -f ~/.weathericons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | tail -n1).png ~/.cache/weather-tomorrow.png}${image ~/.cache/weather-tomorrow.png -p 130,175 -s 30x30}
${goto 60}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | head -n1}${goto 190}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | tail -n1}
${goto 60}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | head -n1}° ${color6}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | head -n1}°${color}${goto 190}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | tail -n1}° ${color6}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | tail -n1}°${color}${voffset 15}
${color5}${hr}${color}
${if_existing /proc/net/route wlan0}
${color4}Up:${color} ${color3}${upspeed wlan0}${color}${alignr}${color1}Down:${color} ${color3}${downspeed wlan0}${color}
${upspeedgraph wlan0 50,120 B3B3B3 B3B3B3}${alignr}${downspeedgraph wlan0 50,120 7A7A7A 7A7A7A}
${color1}Sent:${color} ${color2}${totalup wlan0}${color}${alignr}${color1}Received:${color} ${color2}${totaldown wlan0}${color}
${else}${if_existing /proc/net/route eth0}
${color4}Up:${color} ${color4}${upspeed eth0}${color}${alignr}${color4}Down:${color} ${color4}${downspeed eth0}${color}
${upspeedgraph eth0 50,120 181818 181818}${alignr}${downspeedgraph eth0 50,120 181818 181818}
${color4}Sent:${color} ${color4}${totalup eth0}${color}${alignr}${color4}Received:${color} ${color4}${totaldown eth0}${color}
${else}${if_existing /proc/net/route eth1}
${color4}Up:${color} ${color4}${upspeed eth1}${color}${alignr}${color4}Down:${color} ${color4}${downspeed eth1}${color}
${upspeedgraph eth1 50,120 181818 181818}${alignr}${downspeedgraph eth1 50,120 181818 181818}
${color4}Sent:${color} ${color4}${totalup eth1}${color}${alignr}${color4}Received:${color} ${color4}${totaldown eth1}${color}
${else}${if_existing /proc/net/route ppp0}
${color4}Up:${color} ${color4}${upspeed ppp0}${color}${alignr}${color4}Down:${color} ${color4}${downspeed ppp0}${color}
${upspeedgraph ppp0 50,120 181818 181818}${alignr}${downspeedgraph ppp0 50,120 181818 181818}
${color4}Sent:${color} ${color4}${totalup ppp0}${color}${alignr}${color4}Received:${color} ${color4}${totaldown ppp0}${color}
${else}
Network disconnected
${color3}Connect to a network to see statistics${color}
${voffset 50}
${endif}${endif}${endif}${voffset -15}
${color5}${hr}${color}
${color4}${font Open Sans Light:size=15}System Info
${color4}${font Open Sans Light:pixelsize=10}USER: ${color4}${alignr}${nodename}
${color4}${font Open Sans Light:pixelsize=10}DISTRO:  ${color4}${alignr}${pre_exec lsb_release -sd || cat /etc/*release}
${color4}${font Open Sans Light:pixelsize=10}KERNEL: ${color4}${alignr}${kernel}
${color4}${font Open Sans Light:pixelsize=10}ARCH: ${color4}${alignr}$machine
${color4}${font Open Sans Light:pixelsize=10}CPU: ${color4}${alignr}${freq_g cpu0} GHz
${color4}${font Open Sans Light:pixelsize=10}UPTIME: ${color4}${alignr}${uptime}
${color4}${font Open Sans Light:pixelsize=10}PROCESSES: ${color4}${alignr}$processes ${color4}($running_processes running)
${color5}${hr}${color}
${color4}${font Open Sans Light:size=15}Processors/Memory
${color4}${font Open Sans Light:pixelsize=10}CPU 1: ${color4}${alignc}${freq_g 0} ${color4}Ghz ${color4}${alignr}${cpu cpu0}${color4}%
${color4}${font Open Sans Light:pixelsize=10}CPU 2: ${color4}${alignc}${freq_g 1} ${color4}Ghz ${color4}${alignr}${cpu cpu1}${color4}%
${alignr}${loadgraph 50,250 131313 131313 -l}
${color4}${font Open Sans Light:pixelsize=10}RAM: ${color4}${alignc 10}${mem}
${color4}${font Open Sans Light:pixelsize=10}TOTAL: ${color4}${alignc 10}${memmax}
${font Open Sans Light:pixelsize=10}${color #B3B3B3}CPU TEMP 1: ${color2}${alignr}${execp sensors coretemp-isa-0000 | grep 'Core 0' | cut -c16-17} ${color2}°C${color2} ${color1}/ ${color4}105${color4} °C$color
${font Open Sans Light:pixelsize=10}${color #B3B3B3}CPU TEMP 2: ${color2}${alignr}${execp sensors coretemp-isa-0000 | grep 'Core 1' | cut -c16-17} ${color2}°C ${color1}/ ${color4}105${color4} °C$color
${font Open Sans Light:pixelsize=10}${color #B3B3B3}GPU TEMP: ${color2}${alignr}${execi 60 nvidia-settings -query GPUCoreTemp | perl -ne 'print $1 if /GPUCoreTemp.*?: (\d+)./;'} °C ${color1}/ ${color4}140${color4} °C$color
#${color5}${hr}${color}





```

---

### Post by stinkeye on 2013-05-17
How do you enable wireless and wired at the same time?

Anyway the lines in your conky that determine what is shown are..
```
${if_existing /proc/net/route .....}
```

So open a terminal and see what is shown by...
```
cat /proc/net/route
```

---

### Post by stylintile on 2013-05-17
Hello,
     I tried your conky on my machine.  I had to remove the weather and nvidia parts as I don't use either one, and it looked like it was writing double on the first section.  So I played with the configuration (above "TEXT") and it was still doing it, so I replaced everything above TEXT, except the color and size settings, and it worked perfect.  I'm not sure which particular setting it was, but this is what I use on all of my conky configs and it works for me on XFCE, LXDE and gnome with compiz, with only a couple of changes.  I'm including the config settings below if you would like to try them.  Also, you have one missing endif in there.  And, just in case you didn't know, you can also use;
```
${if_up wlan0}
```
or whichever interface, and add;
```
if_up_strictness address
```
above text.  Then it will only display if the interface is connected AND has an address assigned to it.
Here is my config settings I used for it to display right:
```
max_specials 10000
max_user_text 1500000
background no
use_xft yes
#xftfont Sans:size=12
#xftalpha 1
font Ubuntu Mono:size=10
total_run_times 0
own_window yes
own_window_argb_visual yes
own_window_transparent yes
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250
maximum_width 280
draw_shades no
draw_outline no
draw_borders no
default_bar_size 185 9
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color white
alignment top_left
gap_x 0
gap_y 30
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale yes
text_buffer_size 512
top_name_width 10
if_up_strictness address
update_interval 1

color1 000000 #black
color2 48FF00 #green
color3 B5A100 #yellow
color4 B3B3B3 #silver
color5 7A7A7A #darksilver
color6 00ADA7 #blue
color7 F2D03B

```

I hope this will help

---

