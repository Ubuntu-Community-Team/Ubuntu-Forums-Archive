---
title: "Conky image loading problem"
date: 2010-04-09
forum: Desktop Environments
---

### Post by Tapas Bose, India on 2010-04-09
Hello. This is my conky-weather script :
```

background no
use_xft yes
xftfont Sans:size=9
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 100 50
maximum_width 0
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color black
default_outline_color white
# custom colors #######################################################
color0 FFFFFF
color1 F5F5F5
color2 A2AEC6
color3 696969
color4 D3D3D3
color5 6495ED
color6 87CEFA
color7 5F9EA0
color8 BBBBBB
color9 262729

alignment bottom_right
gap_x 70
gap_y 45
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale yes
##############################################
#  Output
##############################################
TEXT


${voffset -50}{$color4}${font ConkyWeather:size=36}${execi 3600 conkyForecast --location=INXX0300 --datatype=WF}${font Sans:size=10}${goto 70}${voffset -10}Temperature: ${execi 3600 conkyForecast --location=INXX0300 --datatype=HT}

${image [--datatype=MI] -p 280,125 -s 90x90}
${color2}${font}Current Condition: ${execi 600 conkyForecast --location=INXX0300 --datatype=CC}
${color2}${font}Barometer Tendency: ${execi 600 conkyForecast --location=INXX0300 --datatype=BD}
${color2}${font}Barometer Reading: ${execi 600 conkyForecast --location=INXX0300 --datatype=BR}
${color2}${font}Humidity: ${execi 600 conkyForecast --location=INXX0300 --datatype=HM}
${color2}${font}Wind Speed: ${execi 600 conkyForecast --location=INXX0300 --hideunits --datatype=WS} km/h ${execi 600 conkyForecast --location=INXX0300 --hideunits --datatype=WD}
${color2}${font}Wind Gusts: ${execi 600 conkyForecast --location=INXX0300 --datatype=WG}
${color2}${font}Daylight: ${execi 600 conkyForecast --location=INXX0300 --datatype=SR} - ${execi 600 conkyForecast --location=INXX0300 --datatype=SS}
${color2}${font}Visibleness: ${execi 600 conkyForecast --location=INXX0300 --datatype=VI}
${color2}${font}Dew point: ${execi 600 conkyForecast --location=INXX0300 --datatype=DP}
${color2}${font}Moon Phase: ${execi 600 conkyForecast --location=INXX0300 --datatype=MP}
${color2}${font}Precipitation Chance: ${execi 600 conkyForecast --location=INXX0300 --datatype=PC}

```
Whenever I am trying to run it I am getting this output :
```
Conky: desktop window (24000a6) is subwindow of root window (102)
Conky: window type - override
Conky: drawing to created window (0x4c00001)
Conky: desktop window (24000a6) is subwindow of root window (102)
Conky: window type - override
Conky: drawing to created window (0x4a00001)
Conky: desktop window (24000a6) is subwindow of root window (102)
Conky: window type - override
Conky: drawing to created window (0x5800001)
Conky: desktop window (24000a6) is subwindow of root window (102)
Conky: window type - override
Conky: drawing to created window (0x5000001)
Conky: desktop window (24000a6) is subwindow of root window (102)
Conky: window type - override
Conky: drawing to created window (0x4e00001)
Conky: drawing to double buffer
Conky: drawing to double buffer
Conky: drawing to double buffer
Conky: drawing to double buffer
Conky: drawing to double buffer
Conky: Unable to load image '[--datatype=MI]'

```
The image is not displaying. I cannot figure it out. Not only [--datatype=MI], but also [--datatype=WI], [--datatype=BI] etc. Please help. I am in Lucid.

---

### Post by Tapas Bose, India on 2010-05-15
bump.

---

### Post by bra|10n on 2010-05-18
Are you using this to get weather on your desk?

[http://ubuntuforums.org/showthread.php?t=869328&highlight=conky+weather](http://ubuntuforums.org/showthread.php?t=869328&highlight=conky+weather)

If so, you need to call up the template file into conky only, i.e 

${execpi 1800 conkyForecast --location=[COLOR=Red]UKXX0103[/COLOR] --template=/usr/share/conkyforecast/example/conkyForecast.template} - [COLOR=Red]edit to your location[/COLOR]

Let the template do the rest for you ;)

---

### Post by Tapas Bose, India on 2010-05-19
@bra|10n you are right. Actually at first I am trying to write the weather script in the conkyrc, thats why the image loading problem arose, now it is solved. Thank you.

---

