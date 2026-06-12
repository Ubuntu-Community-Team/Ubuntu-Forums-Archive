---
title: "having trouble with conky weather"
date: 2011-03-08
forum: Desktop Environments
---

### Post by Arminius on 2011-03-08
I've just reinstalled Ubuntu, and I've moved all my conky's back over, or at least I think I've moved them all.
And everything is working except for the weather, check the pic out.

So here's the code that conky ```
##################################
## VinDSL | rev. 11-02-17 01:46 ##
##################################
##   Screen res: 1280x1024x24   ##
##################################

####
## Prerequisites (required).
## conky-all 1.8.0 or 1.8.1
## conkyForecast 2.16
## weather.com XML Data Feed (XOAP)
#

####
## Use XFT? Required to Force UTF8 (see below).
#
use_xft yes
xftfont DroidSans:size=8.75
xftalpha 0.1
text_buffer_size 2048

####
## Force UTF8? Requires XFT (see above).
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## Daemonize Conky, aka 'fork to background'.
#
background yes

####
## Update interval in seconds.
#
update_interval 1.5

####
## This is the number of times Conky will update before quitting.
## Set to zero to run forever.
#
total_run_times 0

####
## Create own window instead of using desktop (required in nautilus)?
#
own_window yes
own_window_type override
own_window_transparent yes

####
## Force images to redraw when they change.
#
imlib_cache_size 0

####
## Use double buffering? Reduces flicker.
#
double_buffer yes

####
## Draw shades?
#
draw_shades no

####
## Draw outlines?
#
draw_outline no

####
## Draw borders around text?
#
draw_borders no

####
## Draw borders around graphs?
#
draw_graph_borders yes

####
## Print text to stdout?
## Print text in console?
#
out_to_ncurses no
out_to_console no

####
## Text alignment.
#
alignment bottom_right

####
## Minimum size of text area.
#
minimum_size 340 798

####
## Gap between text and screen borders.
#
gap_x 8
gap_y -75

####
## Shorten MiB/GiB to M/G in stats.
#
short_units yes

####
## Pad % symbol spacing after numbers.
#
pad_percents 0

####
## Pad spacing between text and borders.
#
border_inner_margin 4

####
## Limit the length of names in "Top Processes".
#
top_name_width 10

####
## Subtract file system -/+buffers/cache from used memory?
## Set to yes, to produce meaningful physical memory stats.
#
no_buffers yes

####
## Set to yes, if you want all text to be in UPPERCASE.
#
uppercase no

####
## Number of cpu samples to average.
## Set to 1 to disable averaging.
#
cpu_avg_samples 2

####
## Number of net samples to average.
## Set to 1 to disable averaging.
#
net_avg_samples 2

####
## Add spaces to keep things from moving around?
## Only affects certain objects.
#
use_spacer right

####
## My colors (suit yourself).
#
color0 White
color1 Ivory
color2 Ivory2
color3 Ivory3
color4 Tan1
color5 Tan2
color6 Gray
color7 AntiqueWhite4
color8 DarkSlateGray
color9 Black


####
## Load Lua for bargraphs (required).
## Set the path to your script here.
#
lua_load /.conky/bargraph_small.lua
lua_draw_hook_post main_bars

####
## Installed fonts (required).
#
# ConkyWeather (Stanko Metodiev)
# ConkyWindNESW (Stanko Metodiev)
# Cut Outs for 3D FX (Fonts & Things)
# Droid Font Family (Google Android SDK)
# Moon Phases (Curtis Clark)
# OpenLogos (Icoma)
# PizzaDude Bullets (Jakob Fischer)
# Radio Space (Iconian Fonts)
# StyleBats (Vinterstille)
# Ubuntu (Canonical Ltd)
# Ubuntu Title Bold (Paulo Silva)
# Weather (Jonathan Macagba)

TEXT
##################
##    SYSTEM    ##
##################
${voffset 20}${font DroidSans:bold:size=8.25}${color4}SYSTEM${offset 8}${color8}${voffset -2}${hr 2}${font}
${color brown} Updates Available: ${execi 1800 aptitude search "~U" | wc -l | tail}
${font DroidSans:size=8.65}${offset 5}Ubuntu Version: ${pre_exec lsb_release -r -s}
${font DroidSans:size=8.65}${offset 5}Uptime: $uptime
  Kernel: $kernel
  Conky Build Date: $conky_build_date
  Conky Version: $conky_version
##################
##    TRAFFIC    ##
##################
${voffset 20}${font DroidSans:bold:size=8.25}${color4}INTERNET TRAFFIC${offset 8}${color8}${voffset -2}${hr 2}${font}
${color green}NETWORK IP: ${addr eth1}

DOWN:  ${downspeed eth1}/s                   UP:  ${upspeed eth1}/s  
Today:${goto 65}${execi 300 vnstat -i eth1 | grep "today" | awk '{print $2 $3}'}${goto 150} Today:${goto 210}${execi 300 vnstat -i eth1 | grep "today" | awk '{print $5 $6}'}
Week:${goto 65}${execi 300 vnstat -i eth1 -w | grep "current week" | awk '{print $3 $4}'}${goto 150} Week:${goto 210}${execi 300 vnstat -i eth1 -w | grep "current week" | awk '{print $6 $7}'} 
Month:${goto 65}${execi 300 vnstat -i eth1 -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 150} Month:${goto 210}${execi 300 vnstat -i eth1 -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
Maximum: 100GB                  Maximum:  100GB
Down: ${downspeedgraph eth1 555753 eeeeec}
Up : ${upspeedgraph eth1 555753 eeeeec}
##################
##   WEATHER    ##
##################
${voffset 6}${font DroidSans:bold:size=8}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 0}${goto 59}${font Weather:size=38}${color2}y${font}${voffset -33}${offset 14}${font RadioSpace:size=32}${color3}${execi 1800 conkyForecast -d HT -u}C${font}
${voffset 0}${font Ubuntu:size=24}${color4}${alignc}${execi 1800 conkyForecast -d CT}${font}
${voffset 10}${goto 20}${font ConkyWindNESW:size=41}${color3}${execi 1800 conkyForecast -d BS}${font}${voffset -40}${goto 98}${font ConkyWeather:size=45}${execi 1800 conkyForecast -d WF}${font}${voffset -39}${goto 188}${font MoonPhases:size=32}${execi 1800 conkyForecast -d MF}${font}
${voffset 6}${goto 28}${font DroidSansFallback:bold:size=8.45}${color4}${execpi 1800 conkyForecast -d WS | sed -e 's/calm'/'\$\{offset 2}Calm/g' -e 's/KPH'/'\$\{offset 2}KPH/g'}${goto 88}Feels like ${execi 1800 conkyForecast -d LT -u}${execpi 1800 conkyForecast -d MP| sed -e 's/First.*'/'\$\{goto 182}First Qtr/g' -e 's/Last.*'/'\$\{goto 184}Last Qtr/g' -e 's/New.*'/'\$\{goto 195}New/g' -e 's/Full.*'/'\$\{goto 195}Full/g' -e 's/Waning.*'/'\$\{goto 187}Waning/g' -e 's/Waxing.*'/'\$\{goto 187}Waxing/g'}${font}
${voffset 9}${goto 36}${font DroidSansMono:bold:size=8.35}${color3}${execi 1800 conkyForecast -d DW -s 1 -w}${goto 89}${execi 1800 conkyForecast -d DW -s 2 -w}${goto 143}${execi 1800 conkyForecast -d DW -s 3 -w}${goto 197}${execi 1800 conkyForecast -d DW -s 4 -w}${font}
${voffset 2}${goto 25}${font ConkyWeather:size=32}${color2}${execi 1800 conkyForecast -d WF -s 1 -e 4 -S 1}${font}
${voffset 0}${goto 25}${font DroidSans:bold:size=8.5}${color4}${execi 1800 conkyForecast -d HT -s 1 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 1 -u}${goto 79}${execi 1800 conkyForecast -d HT -s 2 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 2 -u}${goto 133}${execi 1800 conkyForecast -d HT -s 3 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 3 -u}${goto 187}${execi 1800 conkyForecast -d HT -s 4 -u}${offset 2}/${offset 2}${execi 1800 conkyForecast -d LT -s 4 -u}${font}

${font Ubuntu:size=10}${color4}Today's Sunrise: ${color1}${execi 600 conkyForecast --location=ASXX0016 --datatype=SR --}${alignr}${color4} Today's Sunset: ${color1}${execi 600 conkyForecast --location=ASXX0016 --datatype=SS --}
${font Ubuntu:size=10}${color4}Tomorrow's Sunrise: ${color #E6E8FA}${execi 600 conkyForecast --location=ASXX0016 --startday=1 --datatype=SR --}${alignr}${color4} Tomorrow's Sunset: ${color1}${execi 600 conkyForecast --location=ASXX0016 --startday=1 --datatype=SS --}
${font Ubuntu:size=10}${color4}Peak Winter Sunrise: ${color1}05:43 ${alignr}${color4} Peak Winter Sunset: ${color1}18:17
${font Ubuntu:size=10}${color4}Peak Summer Sunrise: ${color1}05:41 ${alignr}${color4} Peak Summer Sunset: ${color1}18:19
${color4}${font Ubuntu:size=10}Station: ${color1}${execi 600 conkyForecast --location=ASXX0016 --datatype=OB}${alignr}${color4}${font Ubuntu:size=10}Last Update: ${color1}${execi 600 conkyForecast --location=ASXX0016 --datatype=LU}${font}
```

I went to /usr/share/conkyforecast and added all my info into conkyForecast.config

but still not getting anything as u can see in the pic

so I entered the details that worked in my old os in so long ago that I can't remember if I missed some key process.

So yes any pointers as to where to look?

---

### Post by Arminius on 2011-03-09
bump

---

### Post by stinkeye on 2011-03-09
The **conkyForecast.config** file needs to be in your home folder
for conkyforecast to work.

Copy as a hidden file to your home directory.
```
cp /usr/share/conkyforecast/conkyForecast.config ~/.conkyForecast.config
```


and to edit
```
gedit ~/.conkyForecast.config
```

P.S. Did you get the gmail.pl script to work?

---

### Post by Arminius on 2011-03-09
yep I have the .conkyForecast.config in my home folder, got all my details inside it.
Still no weather icons working.

and no I haven't gotten gmail to work yet, I'll deal with that when I've solved this

---

### Post by Arminius on 2011-03-09
am I missing a font perhaps, I searched for the others but when I didn't find them I assumed they came with conkyweather package.
here's a screenshot of all the fonts I downloaded, any missing that u can see?

---

### Post by stinkeye on 2011-03-09
Start your conky in the terminal and see what error it's throwing up.
```
conky -c /path/to/your/conky
```

---

### Post by Arminius on 2011-03-09
it returned with ```
conky -c /home/me/.conkyrc
Conky: llua_load: cannot open /.conky/bargraph_small.lua: No such file or directory
Conky: forked to background, pid is 6425
me@mycomputer:~$ 
Conky: desktop window (20000ad) is subwindow of root window (15a)
Conky: window type - override
Conky: drawing to created window (0x6600001)
Conky: drawing to double buffer
Conky: llua_do_call: function conky_main_bars execution failed: attempt to call a nil value
ERROR: Error reading weather data: Invalid License Key.
ERROR: Location ASXX0016 is not in cache.
ERROR: Failed to load the location cache
ERROR: Location ASXX0016 is not in cache.
ERROR: Failed to load the location cache
ERROR: Error reading weather data: Invalid License Key.
ERROR: Location ASXX0016 is not in cache.
ERROR: Failed to load the location cache
ERROR: Location ASXX0016 is not in cache.
ERROR: Failed to load the location cache

```

I copied that license key from the email I got, do they expire, I'll check it and the location code and post my results

---

### Post by Arminius on 2011-03-09
hmmm, license key was same as the one emailed me, so unless it's been cancelled that's not the problem
and my city's location code was right to.
I'm in brisbane, australia, and that's ment to be ASXX0016

so still not getting it.

---

### Post by stinkeye on 2011-03-09
If you run 
```
gedit ~/.conkyForecast.config
```
does the file open?

---

### Post by Arminius on 2011-03-10
yep it opens if I run that code in terminal

---

### Post by Arminius on 2011-03-11
bump

---

### Post by Legeril on 2011-03-11
I would advise taking all your conkyForecast troubles over to the offical thread [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)

it's checked regularly and the guys there are great

---

