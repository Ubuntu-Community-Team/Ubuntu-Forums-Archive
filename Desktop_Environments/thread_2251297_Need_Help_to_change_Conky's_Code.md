---
title: "Need Help to change Conky's Code"
date: 2014-11-03
forum: Desktop Environments
---

### Post by cyber-souza on 2014-11-03
Hy,

i need help, i'm beginner in descovery conky's code, and  ilive in Brasil, the conky above is like of one that i heve  downloaded,but these's one thing i want to change, the location and  langange. The first i did, i just placed the code of my country, however  the words continues displays in english,but i wanted this in portugues.  Does anyone help me? The code is the below.

P.S.:Sorry about my poor english!

```
# Conky settings #
background no
update_interval 100
double_buffer yes
no_buffers yes

# Window specifications #
own_window yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_title 
own_window_colour 000000
own_window_argb_visual yes
own_window_argb_value 0

minimum_size 259 239
maximum_width 259 239
# Alignment #
alignment middle_middle
gap_x 3
gap_y 77

border_inner_margin 12
border_outer_margin 0

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftalpha 0
xftfont Open Sans Light:size=10

override_utf8_locale yes

imlib_cache_size 0

# Color scheme #
default_color 333333

color1 0099CC
color2 9933CC
color3 669900
color4 FF8800
color5 CC0000
color6 AAAAAA
color7 DDDDDD

own_window_transparent yes
TEXT
Agora: ${execi 300 curl -s **"http://weather.yahooapis.com/forecastrss?w=[COLOR=#ff0000]455826 (this is the country's code, it's, i changed it and solved it) [/COLOR]**&u=c" -o ~/.cache/weather.xml}
${alignr  30}${voffset -30}${font Open Sans Light:size=11}${voffset 10}${execi  300 grep "yweather:condition" ~/.cache/weather.xml | grep -o  "text=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | tr '[a-z]'  '[A-Z]'}${font}
${voffset 5}${offset 10}${font Open Sans  Light:size=56}${execi 300 grep "yweather:condition" ~/.cache/weather.xml  | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o  "[^\"]*"}°${font}${voffset -23}
${execi 300 cp -f  ./conky_icons/$(grep "yweather:condition" ~/.cache/weather.xml | grep -o  "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*").png  ~/.cache/weather.png}${image ~/.cache/weather.png -p 190,35 -s 60x60}
${image  ./conky_icons/wind.png -p 224,107 -s 15x15}${alignr 40}${execi 300 grep  "yweather:wind" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" |  grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}${execi 300 grep  "yweather:units" ~/.cache/weather.xml | grep -o "speed=\"[^\"]*\"" |  grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}
${image  ./conky_icons/humidity.png -p 224,127 -s 15x15}${alignr 40}${execi 300  grep "yweather:atmosphere" ~/.cache/weather.xml | grep -o  "humidity=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}%
${color6}${hr}${color}
Previsão  de Metereologia:${execi 300 cp -f ./conky_icons/$(grep  "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" |  grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1').png  ~/.cache/weather-1.png}${image ~/.cache/weather-1.png -p 6,190 -s  30x30}${execi 300 cp -f ./conky_icons/$(grep "yweather:forecast"  ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" |  grep -o "[^\"]*" | awk 'NR==2').png ~/.cache/weather-2.png}${image  ~/.cache/weather-2.png -p 57,190 -s 30x30}${execi 300 cp -f  ./conky_icons/$(grep "yweather:forecast" ~/.cache/weather.xml | grep -o  "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk  'NR==3').png ~/.cache/weather-3.png}${image ~/.cache/weather-3.png -p  108,190 -s 30x30}${execi 300 cp -f ./conky_icons/$(grep  "yweather:forecast" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" |  grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==4').png  ~/.cache/weather-4.png}${image ~/.cache/weather-4.png -p 159,190 -s  30x30}${execi 300 cp -f ./conky_icons/$(grep "yweather:forecast"  ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" |  grep -o "[^\"]*" | awk 'NR==5').png ~/.cache/weather-5.png}${image  ~/.cache/weather-5.png -p 210,190 -s 30x30}
${goto 18}${voffset  45}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o  "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1'  | tr '[a-z]' '[A-Z]'}${goto 71}${execi 300 grep "yweather:forecast"  ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" |  grep -o "[^\"]*" | awk 'NR==2' | tr '[a-z]' '[A-Z]'}${goto 124}${execi  300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o  "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==3'  | tr '[a-z]' '[A-Z]'}${goto 177}${execi 300 grep "yweather:forecast"  ~/.cache/weather.xml | grep -o "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" |  grep -o "[^\"]*" | awk 'NR==4' | tr '[a-z]' '[A-Z]'}${goto 230}${execi  300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o  "day=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==5'  | tr '[a-z]' '[A-Z]'}${voffset -49}
```

---

### Post by overdrank on 2014-11-03
Moved to Desktop Environments

---

