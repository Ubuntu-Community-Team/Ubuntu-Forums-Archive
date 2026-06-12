---
title: "Couple of random problems Conky - Crash reports"
date: 2012-07-29
forum: Desktop Environments
---

### Post by geekyhawkes on 2012-07-29
Couple of random problems Conky - Crash reports

Hey guys, so Im having problems working out why the following happens on my 12.04 64bit xubuntu install:

1) sometimes i have to run .startconky myself, other times the system runs 2 versions of conky itself! In Session and startup of settings manager there is only one entry to my .startconky script, what have i missed? Its annoying having to top / sudo kill a conky each time the system starts. Of late it seems to start 2 versions more than not start any.

2) When my machine starts it says there are crash reports being generated, where are these logs saved so I can look at them and work out what is failing?

Any help well received!

---

### Post by Toz on 2012-07-29
> **geekyhawkes said:**
> Couple of random problems Conky - Crash reports

Hey guys, so Im having problems working out why the following happens on my 12.04 64bit xubuntu install:

1) sometimes i have to run .startconky myself, other times the system runs 2 versions of conky itself! In Session and startup of settings manager there is only one entry to my .startconky script, what have i missed? Its annoying having to top / sudo kill a conky each time the system starts. Of late it seems to start 2 versions more than not start any.
In Xfce, when you save a session (check box on logout screen or manually from Settings Manager -> Session and startup -> Session) conky will be saved and automatically restarted on the next session. If you also have conky starting in autostart, you'll end up with two instances. Either start conky using autostart (and don't use saved sessions), or remove conky from autostart and let saved sessions restart it.

> 2) When my machine starts it says there are crash reports being generated, where are these logs saved so I can look at them and work out what is failing?
/var/log/apport.log and friends.

---

### Post by geekyhawkes on 2012-07-30
Thanks, so the conky thing might be something to do with the following from my /var/log/apport.log 

```
ERROR: apport (pid 2301) Mon Jul 30 08:35:12 2012: executable: /usr/bin/conky (command line "conky -c /home/geeky/Conky/.conkyrc")
ERROR: apport (pid 2301) Mon Jul 30 08:35:12 2012: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

ERROR: apport (pid 2301) Mon Jul 30 08:35:12 2012: debug: session gdbus call: 
ERROR: apport (pid 2301) Mon Jul 30 08:35:12 2012: apport: report /var/crash/_usr_bin_conky.1000.crash already exists and unseen, doing nothing to avoid disk usage DoS
ERROR: apport (pid 2479) Mon Jul 30 08:35:41 2012: called for pid 2472, signal 11
ERROR: apport (pid 2479) Mon Jul 30 08:35:41 2012: executable: /usr/bin/conky (command line "conky -c /home/geeky/Conky/.conkyrc")
ERROR: apport (pid 2479) Mon Jul 30 08:35:41 2012: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

ERROR: apport (pid 2479) Mon Jul 30 08:35:41 2012: debug: session gdbus call: 
ERROR: apport (pid 2479) Mon Jul 30 08:35:41 2012: apport: report /var/crash/_usr_bin_conky.1000.crash already exists and unseen, doing nothing to avoid disk usage DoS
```

??

---

### Post by Toz on 2012-07-30
Well, conky is definitely crashing. Try fixing the problem with 2 instances of conky starting and see if the crashes stop.

---

### Post by geekyhawkes on 2012-07-30
Its odd, sometimes i get no instances of conky though.  So I have selected to save sessions now and I just get the crash report with no instances of conky, so its sort of sorted i guess.  Just need to get to the bottom of why its crashing now.  I had a look at /var/crash/_usr_bin_conky.1000.crash  but it doesnt seem to give much that i could work out WHY from?

---

### Post by Toz on 2012-07-30
Perhaps you could post a copy of your conky config file and get a second set of eyes to give it a once over?

---

### Post by geekyhawkes on 2012-07-31
Sure, thanks for the offer, conkyrc reads as follows:

```
##################################
## VinDSL | rev. 11-12-01 20:20 ##
##################################
##     December 2011 Series     ##
##################################

## ¡PLEASE READ THE FINE PRINT! ##

####
## Development Platforms (current)
#
#  Ubuntu 10.10 'Maverick Meerkat' (GNOME 2.28 - Conky 1.8.0)
#  Ubuntu 12.04 'Precise Pangolin' (GNOME-SHELL - UNITY 2D/3D - Conky 1.8.1)
#  Screen Resolution: 1280x1024x24 (DELL UltraSharp 1907FP)

####
## Prerequisites (required)
#
#  conky-all 1.8.0 or 1.8.1
#  cURL - Command Line Tool
#  xsltproc - Command Line Tool
#  UTF-8 Compatible Text Editor

####
## Installed fonts (required)
#
#  ConkyWeather (Stanko Metodiev)
#  Cut Outs for 3D FX (Fonts & Things)
#  Droid Font Family (Google Android SDK)
#  KR A Round (Kat's Fun Fonts)
#  OpenLogos (Icoma)
#  PizzaDude Bullets (Jakob Fischer)
#  Radio Space (Iconian Fonts)
#  StyleBats (Vinterstille)
#  Ubuntu Font Family (Canonical Ltd)
#  Ubuntu Title Bold (Paulo Silva - not included in link below)
#  Weather (Jonathan Macagba)
# 
## Tips n' Tricks from Mr. Peachy, djyoung4, and 42dorian (Thanks!)
## Most necessary fonts can be downloaded here: http://ompldr.org/vOHdoag
## Unzip the fonts into your font folder, for example: /home/username/.fonts
## Run this command in a terminal (rebuilds font cache file): sudo fc-cache -fv

####
## Use XFT? Required to Force UTF8 (see below)
#
use_xft yes
xftfont DroidSans:size=8.75
xftalpha 0.1

####
## Force UTF8? Requires XFT (see above)
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## This buffer is used for text, single lines, output from $exec, and other variables.
## Increasing the text buffer size (too high) will drastically reduce Conky's performance.
## Decreasing the size (too low) will truncate content and cause strange display output.
## Standard text buffer size is 256 bytes (cannot be less). Adjust YOUR buffer wisely!
#
text_buffer_size 640

####
## Daemonize Conky, aka 'fork to background'.
#
background yes

####
## Update interval in seconds.
#
update_interval 2.0

####
## The number of times Conky will update before quitting.
## Zero makes Conky run forever.
#
total_run_times 0

####
## Create own window in instead of using desktop?
#
own_window yes
own_window_transparent yes
own_window_type normal
own_window_class conky-semi
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
####
## Some distros also require the following 2 lines.
#
own_window_argb_visual yes
own_window_argb_value 255

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
draw_shades yes
default_shade_color 292421

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
draw_graph_borders no

####
## Print text to stdout?
## Print text in console?
#
out_to_ncurses no
out_to_console no

####
## Text alignment.
#
alignment top_right

####
## Minimum size of the text area.
## Syntax: minimum_size [width] [height]
#
# old minimum_size 240 1394
minimum_size 240 1440

####
## Maximum width of the text area.
## Syntax: maximum_width [width]
#
maximum_width 240

####
## Gap between text and screen borders.
#
gap_x 6	  ## Left / Right
gap_y 10  ## Top / Bottom

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
## My colors (suit yourself)
#
color0 White		#FFFFFF
color1 Ivory		#FFFFF0
color2 Ivory2		#EEEEE0
color3 Ivory3		#CDCDC1
color4 Tan1		#FFA54F
color5 Tan2		#EE9A49
color6 Gray		#7E7E7E
color7 AntiqueWhite4	#8B8378
color8 DimGray		#696969
color9 Tomato		#FF6347

#####
## Load Lua for shading (optional)
## Set the path to your script here.
#
lua_load ~/Conky/draw_bg.lua
lua_draw_hook_pre draw_bg

####
## Load Lua for bargraphs (required)
## Set the path to your script here.
#
lua_load ~/Conky/bargraph.lua
lua_draw_hook_post main_bars

TEXT
##################################
##             LOGO             ##
##################################
## Uncomment for hard-coded ID (static)
#${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}1${offset 1}2${offset 1}.${offset 0}0${offset 0}4${font}
####
## Uncomment for soft-coded ID (dynamic)
${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}${pre_exec cat /etc/*release | grep 'RELEASE' | awk -F'=' '{print $2}'}${font}
####
## Additional ID (branch version, code name, release date, etc.)
${voffset -1}${goto 188}${font Ubuntu-B:size=7.1}${color4}by GEEK${font}
##################################
##            SYSTEM            ##
##################################
${voffset 7}${font DroidSans:bold:size=8.25}${color4}SYSTEM${offset 8}${color8}${voffset -2}${hr 2}${font}
# ${voffset 4}${font OpenLogos:size=10}${color2}u${voffset -4}${font DroidSans:size=8.6}${color3}${offset 5}${pre_exec lsb_release -sd || cat /etc/*release}${font}
${voffset 2}${offset -2}${font OpenLogos:size=12}${color2}Z${voffset -4}${font DroidSans:size=8.6}${color3}${offset 3}${sysname}${offset 3}${kernel}${alignr}${font DroidSans:size=8.3}${machine}${font}
${voffset 2}${font StyleBats:size=10}${color2}d${voffset -2}${font DroidSans:size=8.6}${color3}${offset 5}nVidia GeForce 8300 ${alignr}${font DroidSans:size=8.3}${pre_exec dpkg --status nvidia-current | grep Version | cut -f 1 -d '-' | sed 's/[^.,0-9]//g'}${font}
${voffset 2}${font StyleBats:size=10}${color2}A${voffset -1}${font DroidSans:size=8.6}${color3}${offset 5}AMD Athlon${offset 3}Dual Core${offset 3}5050e${offset 3}${alignr 1}${font DroidSans:size=8.3}${freq_g cpu0}${offset 1}GHz${font}
${voffset 2}${font StyleBats:size=10}${color2}q${voffset -1}${font DroidSans:size=8.6}${color3}${offset 5}System${offset 3}Uptime${alignr}${font DroidSans:size=8.3}${uptime_short}${font}
##################################
##          PROCESSORS          ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}PROCESSORS${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CORE1${offset 5}${font DroidSans:size=8.3}${cpu cpu1}%${font}
${voffset 2}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CORE2${offset 5}${font DroidSans:size=8.3}${cpu cpu2}%${font}
##################################
##            MEMORY            ##
##################################
${voffset 5}${font DroidSans:bold:size=8}${color4}MEMORY${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color2}l${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 3}RAM${goto 97}${font DroidSans:size=8.3}${mem}${goto 133}/${offset 5}${memmax}${alignr}${memperc}%${font}
##################################
##             HDD              ##
##################################
${voffset 15}${font DroidSans:bold:size=8}${color4}HDD${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}ROOT${goto 95}${font DroidSans:size=8.3}${fs_used /}${goto 133}/${offset 5}${fs_size /}${alignr}${fs_free_perc /}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}NAS${goto 95}${font DroidSans:size=8.3}${fs_used /media/nas}${goto 133}/${offset 5}${fs_size /media/nas}${alignr}${fs_free_perc /media/nas}%${font}
${voffset 15}${font StyleBats:size=9.9}${color2}4${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}SWAP${goto 95}${font DroidSans:size=8.3}${swap}${goto 133}/${offset 5}${swapmax}${alignr}${swapperc}%${font}
##################################
##         TOP PROCESSES        ##
##################################
${voffset 15}${font DroidSans:bold:size=8}${color4}TOP PROCESSES${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 1}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 1}${alignr}${top_mem mem 1}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 2}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 2}${alignr}${top_mem mem 2}%${font}
${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 3}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 3}${alignr}${top_mem mem 3}%${font}
# ${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 4}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 4}${alignr}${top_mem mem 4}%${font}
# ${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 5}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 5}${alignr}${top_mem mem 5}%${font}
# ${voffset 1}${font StyleBats:size=10}${color1}h${voffset -1}${font DroidSans:size=8.65}${color3}${offset 5}${top_mem name 6}${goto 120}${font DroidSans:size=8.3}${top_mem mem_res 6}${alignr}${top_mem mem 6}%${font}
##################################
##           NETWORK            ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}T${font DroidSans:size=8.65}${color3}${offset 5}Download${goto 120}${font DroidSans:size=8.3}${totaldown eth1}${alignr}${font DroidSans:size=8.3}${downspeed eth1}${font}
${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}N${font DroidSans:size=8.65}${color3}${offset 5}Upload${goto 120}${font DroidSans:size=8.3}${totalup eth1}${alignr}${font DroidSans:size=8.3}${upspeed eth1}${font}
${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Private${offset 3}IP${goto 123}${font DroidSansFallback:size=8.5}Eth1${alignr}${font DroidSans:size=8.3}${addr eth1}${font}
${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Public${offset 7}IP${goto 121}${font DroidSansFallback:size=8.5}WAN${alignr}${font DroidSans:size=8.3}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}${font}
##################################
##     WEATHER (Imperial)       ##
##################################
# ${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
# ${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 ~/Conky/weather/weather.sh "Scottsdale,AZ" ctbi}${font}${voffset -28}${goto 33}${font Weather:size=42}${color3}y${font}
# ${voffset -38}${font Ubuntu:size=8.63}${color5}${execi 1800 ~/Conky/weather/weather.sh "Scottsdale,AZ" ctti}${font}
# ${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
# ${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 ~/Conky/weather/weather.sh "Scottsdale,AZ" ccb}${font}
# ${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 ~/Conky/weather/weather.sh "Scottsdale,AZ"}${font}
# ${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 ~/Conky/weather/weather.sh "Scottsdale,AZ" cp}${font}
# ${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 ~/Conky/weather/weather.sh "Scottsdale,AZ" dl}${font}
# ${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 ~/Conky/weather/weather.sh "Scottsdale,AZ" fcp}${font}
# ${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 28}${execi 1800 ~/Conky/weather/weather.sh "Scottsdale,AZ" fcti}${font}
##################################
##      WEATHER (Metric)        ##
##################################
${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 ~/Conky/weather/weather.sh "Lincoln,UK" ctbm}${font}${voffset -28}${goto 33}${font Weather:size=42}${color3}y${font}
${voffset -38}${font Ubuntu:size=8.63}${color5}${execi 1800 ~/Conky/weather/weather.sh "Lincoln,UK" cttm}${font}
${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 ~/Conky/weather/weather.sh "Lincoln,UK" ccb}${font}
${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 ~/Conky/weather/weather.sh "Lincoln,UK"}${font}
${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 ~/Conky/weather/weather.sh "Lincoln,UK" cp}${font}
${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 ~/Conky/weather/weather.sh "Lincoln,UK" dl}${font}
${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 ~/Conky/weather/weather.sh "Lincoln,UK" fcp}${font}
${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 35}${execi 1800 ~/Conky/weather/weather.sh "Lincoln,UK" fctm}${font}
##################################
##             TIME             ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}TIME${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset -4}${font RadioSpace:size=32}${color3}${if_match ${time %l}<=9}${alignc 7}${time %l:%M%p}${else}${if_match ${time %l}>=10}${alignc -1}${time %l:%M%p}${endif}${endif}${font}
##################################
##      CALENDAR (5-Line)       ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}DATE${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 18}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %A}${font}
${voffset -4}${font DroidSansFallback:bold:size=18}${if_match ${time %e}<=9}${color5}${alignc 65}${time %e}${font}${else}${if_match ${time %e}>=10}${color5}${alignc 60}${time %e}${endif}${endif}${font}
${voffset 0}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %B}${font}
${voffset 0}${font DroidSansMono:size=7.6}${color3}${alignc 60}${time %Y}${font}
${voffset -83}${font CutOutsFor3DFX:size=67}${color8}${alignc 99}2${font}
####
## Uncomment for Conky 1.8.0 (use mono fonts only)
# ${voffset -68}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; cal -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e s/^/"\$\{offset 100"\}/ -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}
####
## Uncomment for Conky 1.8.1 (use mono fonts only)
${voffset -64}${offset 100}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; cal -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}
##################################
##   RHYTHMBOX (Experimental)   ##
##################################
${if_running rhythmbox}
${voffset -8}${font DroidSans:bold:size=7.75}${color4}RHYTHMBOX${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 8}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`/usr/bin/rhythmbox-client --print-playing-format %tt | head -n 1`"}" >= "48"}${alignr 15}${scroll 38 4* ${execi 2 rhythmbox-client --print-playing-format %tt --no-start}}${font}${else}${alignc}${execi 2 rhythmbox-client --print-playing-format %tt --no-start}${font}${endif}${endif}
##################################
##    BANSHEE (Experimental)    ##
##################################
${if_running banshee}
${voffset -10}${font DroidSans:bold:size=7.75}${color4}BANSHEE${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`/usr/bin/banshee --query-title --no-present | cut -f1- -d " "`"}" >= "48"}${alignr 15}${scroll 38 4* ${execi 2 banshee --query-title --no-present | cut -f2- -d " "}}${font}${else}${alignc}${execi 2 banshee --query-title --no-present | cut -f2- -d " "}${font}${endif}${endif}


```

Im not sure there is anything wrong with the conkyrc as when i start conky manually it runs just fine?

Just for completeness, here is my .startconky

```
#!/bin/bash
sleep 0 &&	# 0 good for Xfce - use 20 to 30 for Gnome
conky -c ~/Conky/.conkyrc &
#sleep 0 &&
#conky -c ~/Conky/conkyforecast &
```

---

### Post by Toz on 2012-07-31
> **geekyhawkes said:**
> 
Im not sure there is anything wrong with the conkyrc as when i start conky manually it runs just fine?

It might be that the crash is the result of having two instances of this script running at the same time - especially since running it manually (once) is fine.

---

