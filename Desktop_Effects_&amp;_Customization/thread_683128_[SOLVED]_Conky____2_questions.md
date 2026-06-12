---
title: "[SOLVED] Conky    2 questions"
date: 2008-01-30
forum: Desktop Effects &amp; Customization
---

### Post by jryprt on 2008-01-30
I got one fixed 
Need weather to display 
[COLOR="Blue"]Look at post #5[/COLOR]

---

### Post by jryprt on 2008-01-31
Anyone?

---

### Post by jryprt on 2008-01-31
I got Conky on the top left, 
Still need help with the weather.

---

### Post by Crinos512 on 2008-01-31
[http://ubuntuforums.org/showthread.php?t=666842](http://ubuntuforums.org/showthread.php?t=666842)

seek and ye shall find. :D

---

### Post by jryprt on 2008-01-31
I have the weather.sh in   /home/jerry/conky/weather   
I have the conky file in    /home/jerry/.conkyrc
Here they are does anyone see way I cannot get weather to display?
```
#!/bin/sh

#
# Grab weather data from weather.com and format it according to the given XSLT
# Script written by boojit
# Modified by Hellf[i]re
# The orignal script and xslt can be downloaded from http://pondol.com/weather.tar.gz

# Usage:
# ${execi 1800 /path/to/weather/weather.sh location}
# Usage Example:
# ${execi 1800 /home/user/weather/weather.sh 03833}

# your Location ID: use http://xoap.weather.com/search/search?where=[yourcity] to find it 
# U.S. users can just use their zip code; doubt that works for anyone else though (YMMV)
LOCID=51501

# s=standard units, m=metric units
UNITS=s

# where this script and the XSLT lives
RUNDIR=/home/jerry/conky 

# there's probably other stuff besides CURL that will work for this, but i haven't 
# tried any others. 
# you can get curl at http://curl.haxx.se/
CURLCMD=/usr/bin/curl

# get it at http://xmlsoft.org/XSLT/
XSLTCMD=/usr/bin/xsltproc

# you probably don't need to modify anything below this point....

# CURL url. Use cc=* for current forecast or dayf=10 to get a multi-day forecast
CURLURL="http://xoap.weather.com/weather/local/$LOCID?cc=*&unit=$UNITS&dayf=2"

# The XSLT to use when translating the response from weather.com
# You can modify this xslt to your liking 
XSLT=$RUNDIR/weather.xslt 

#filter (if you want to convert stuff to lower-case or upper case or something)
#FILTER="|gawk '{print(tolower(\$0));}'"


#####
eval "$CURLCMD \"$CURLURL\" 2>/dev/null| $XSLTCMD $XSLT - $FILTER"
```

```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=9

# Text alpha when using Xft
xftalpha 0.9

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 185 5

# Maximum width
maximum_width 185

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders no

# Stippled borders?
# stippled_borders 8

# border margins
# border_margin 2

# border width
# border_width 1

# Default colors and also border colors
default_color white
default_shade_color red
default_outline_color green

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen


TEXT
${color #88ECE0}SYSTEM ${hr 2}$color
 $nodename   $sysname 
 $kernel  on $machine 
${color #88ECE0}CPU ${hr 2}$color
 Current Speed:   ${freq}MHz   
 Load:${alignr}${loadavg}
 Uptime:${alignr}${uptime}
 ${color}Core 1 Usage:$color ${alignc} ${cpu cpu1}% ${color #EEEEEE}${cpubar cpu1}
 ${color}Core 2 Usage:$color ${alignc} ${cpu cpu2}% ${color #EEEEEE}${cpubar cpu2}
 ${cpugraph 000000 FFFF00}
 CPU                ${alignr}CPU%     MEM%
 ${top name 1}${alignr}${top cpu 1}    ${top mem 1}
 ${top name 2}${alignr}${top cpu 2}    ${top mem 2}
 ${top name 3}${alignr}${top cpu 3}    ${top mem 3}
 
 MEM              ${alignr}CPU%     MEM%
 ${top_mem name 1}${alignr}${top_mem cpu 1}    ${top_mem mem 1}
 ${top_mem name 2}${alignr}${top_mem cpu 2}    ${top_mem mem 2}
 ${top_mem name 3}${alignr}${top_mem cpu 3}    ${top_mem mem 3}

${color #88ECE0}MEMORY / DISK ${hr 2}$color
 RAM:   $mem/$memmax - ${alignr}$memperc%
 ${color #EEEEEE}${membar 6}$color
 ROOT:  ${fs_used /}/${fs_size /}${alignr} -   ${fs_used_perc /}%   
 ${color #EEEEEE}${fs_bar 6 /}$color 
 ${color}DiskI/O:${color}${diskio} 
 ${diskiograph 000000 FFCC33}

${color #88ECE0}LOCAL WEATHER: ${hr 2}
${color}${execi 1800 /home/jerry/conky/weather/weather.sh 51501}
```

---

### Post by jryprt on 2008-02-01
I got it . I had to put the weather.sh  & weather.xslt  in /home/jerry/conky  not /home/jerry/conky/weather

Than changed ```
${color #88ECE0}LOCAL WEATHER: ${hr 2}
${color}${execi 1800 /home/jerry/conky/weather/weather.sh 51501}
```

To This ```
${color #88ECE0}LOCAL WEATHER: ${hr 2}
${color}${execi 1800 /home/jerry/conky/weather.sh 51501}
```

---

