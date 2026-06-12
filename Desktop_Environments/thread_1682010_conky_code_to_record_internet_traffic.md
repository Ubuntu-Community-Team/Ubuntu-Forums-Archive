---
title: "conky code to record internet traffic?"
date: 2011-02-05
forum: Desktop Environments
---

### Post by Arminius on 2011-02-05
this is the conky code I found, that displays on conky the way I like, problem is everything shows as 0bytes, and stays that way.

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
#

# Create own window instead of using desktop (required in nautilus)
# own_window yes
# own_window_type override
background no
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont LiberationSans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5
# maximum_width 300

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 0

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color e5e5e5
color0 66cccc # 'header' color

own_window_colour brown

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 20
gap_y 30

# Rounded corners and 'transparency' w/cairo
lua_load ~/.conky/draw_bg.lua
lua_draw_hook_pre draw_bg

#${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
# ********************************************************************************* #
# stuff after 'TEXT' will be formatted on screen
TEXT


${voffset -20}Ubuntu: 10.10 "Maverick Meerkat"
Kernel: $kernel
Uptime: $uptime
Updates Available: ${execi 1200 aptitude search "~U" | wc -l | tail}

$color0${font UbuntuTitleBold:size=9}CPU${font} ${hr 2}$color
${freq}MHz   Load: ${loadavg}
${font StyleBats:size=15}${font}CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 6,248}
${font StyleBats:size=15}${font}CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 6,248}

NAME${alignr 9}PID     CPU%   MEM%
${top name 1}${alignr 9}${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2}${alignr 9}${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3}${alignr 9}${top pid 3}   ${top cpu 3}    ${top mem 3}

$color0${font UbuntuTitleBold:size=9}MEMORY${font} ${hr 2}$color
RAM:   $memperc%   ${alignr}${membar 6,220}$color
Swap:  $swapperc%   ${alignr}${swapbar 6,220}$color

NAME${alignr 9}PID     CPU%   MEM%
${top_mem name 1}${alignr 9}${top_mem pid 1}   ${top_mem cpu 1}    ${top_mem mem 1}
${top_mem name 2}${alignr 9}${top_mem pid 2}   ${top_mem cpu 2}    ${top_mem mem 2}
${top_mem name 3}${alignr 9}${top_mem pid 3}   ${top_mem cpu 3}    ${top_mem mem 3}

$color0${font UbuntuTitleBold:size=9}DISK${font} ${hr 2}$color
Root:  ${fs_used_perc /}%   ${alignr}${fs_bar 6,246 /}$color
Ext Videos:  ${fs_used_perc /media/Ext Videos}%   ${alignr}${fs_bar 6,219 /media/Ext Videos}$color
Ext VID1.5:  ${fs_used_perc /media/Ext VID1.5}%   ${alignr}${fs_bar 6,218 /media/Ext VID1.5}$color
Internal Video:  ${fs_used_perc /media/INTERNAL VI}%   ${alignr}${fs_bar 6,203 /media/INTERNAL VI}$color
Ext Backup1:  ${fs_used_perc /media/Ext Backup1}%   ${alignr}${fs_bar 6,210 /media/Ext Backup1}$color
HTC Legend:  ${fs_used_perc /media/900E-A67B}%   ${alignr}${fs_bar 6,218 /media/900E-A67B}$color
${diskiograph 555753 eeeeec}

##################
##   NETWORK    ##
##################
${voffset 6}${font WenQuanYiMicroHei:bold:size=8.75}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}a${font}${color6}${offset 5}Private${offset 3}IP${alignr}${addr eth0}
${font PizzaDudeBullets:size=10}${color2}a${font}${color6}${offset 5}Public${offset 7}IP${alignr}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}T${font}${color6}${offset 5}Down${alignr}${downspeed eth0}
${font PizzaDudeBullets:size=10}${color2}N${font}${color6}${offset 5}Up${alignr}${upspeed eth0}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}T${font}${color6}${offset 5}Downloaded${alignr}${totaldown eth0}
${font PizzaDudeBullets:size=10}${color2}N${font}${color6}${offset 5}Uploaded${alignr}${totalup eth0}
```

with this part being the code I'm most interested in ```
##################
##   NETWORK    ##
##################
${voffset 6}${font WenQuanYiMicroHei:bold:size=8.75}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}a${font}${color6}${offset 5}Private${offset 3}IP${alignr}${addr eth0}
${font PizzaDudeBullets:size=10}${color2}a${font}${color6}${offset 5}Public${offset 7}IP${alignr}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}T${font}${color6}${offset 5}Down${alignr}${downspeed eth0}
${font PizzaDudeBullets:size=10}${color2}N${font}${color6}${offset 5}Up${alignr}${upspeed eth0}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}T${font}${color6}${offset 5}Downloaded${alignr}${totaldown eth0}
${font PizzaDudeBullets:size=10}${color2}N${font}${color6}${offset 5}Uploaded${alignr}${totalup eth0}
```

so does anyone know what's wrong with it? or can you suggest some code that would work better?

---

### Post by ajgreeny on 2011-02-05
Mine's much simpler than yours and will look very different, but it may give you a clue about editing your network text.
```
${color black}NETWORK IP:${color #7A0756} $alignr wlan0-   ${color #7A0756}${addr wlan0}

${color black}DOWN ${color #7A0756}  ${downspeed wlan0}/s  $alignr${totaldown wlan0}
${color #7A0756}${downspeedgraph wlan0 20,220 000000 #7A0756}
${color black} UP ${color #7A0756}  ${upspeed wlan0}/s  $alignr${totalup wlan0}  
${color #7A0756}${upspeedgraph wlan0 20,220 000000 #7A0756}
```
EDIT: Just a thought; have you got the **eth0** correct?  Depending on your setup it may be wlan0 like mine if wireless, or eth1.  Right click on your network manager or choose edit connections to see what is active, and use ```
ifconfig
``` to find it

---

### Post by Arminius on 2011-02-05
thank u, feel like an idiot but it has eth0, but I was using eth1,
so changed that and now it's working fine.
Your code is much better then I had, so I'm using that
But I think it's only displaying how much I've downloaded since I've booted up, 52MB, which is way way to small, how can I get it to remember how much has been downloaded since my ISP reset on the 3rd of this month?
Is that to complex for conky?

---

### Post by ajgreeny on 2011-02-05
It may be possible to get conky to display the output of **vnstat**, if you have it installed, but I've never tried it.  Have a look at man **vnstat**, and you'll see there are a number of different output layouts you can choose, for days, weeks, months, etc etc.  It is very useful, but as for conky displaying it, I haven't a clue.

---

### Post by Arminius on 2011-02-05
I followed the instructions on the first picture attached "screenshot"
and everything happened like the writer said it would.
But when I add the code as instructed ```
${goto 10}${font DejaVu Sans Mono:bold:size=9}  ${color5}Ayer:${color3} ${execi 300 vnstat | grep "yesterday" | awk '{print $2 $3}'}${goto 140}${color9}${execi 300 vnstat | grep "yesterday" | awk '{print $5 $6}'}${goto 205}${color5}${execi 300 vnstat | grep "yesterday" | awk '{print $8 $9}'}
${goto 10}   ${color5}Hoy:${color3} ${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${goto 140}${color9}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}${goto 205}${color5}${execi 300 vnstat | grep "today" | awk '{print $8 $9}'}
${goto 10}${color5}Semana: ${color3}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${goto 140}${color9}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'}${goto 205}${color5}${execi 300 vnstat -w | grep "current week" | awk '{print $9 $10}'}
${goto 10}   ${color5}Mes: ${color3}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 140}${color9}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}${goto 205}${color5}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $9 $10}'}${font}
```

but all that's come out is what's in screenshot2, so where am I going wrong?

---

### Post by ajgreeny on 2011-02-06
OK, here's the TEXT part of my .conkyrc file that gives me a good output of day, week and month DOWN and UP figures.
          ```
DOWN:                    $alignr UP:          
${color #56073D}Today: ${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${alignr}Today: ${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}  
${color #56073D}Week:  ${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${alignr}Week:  ${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'} 
${color #56073D}Month: ${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${alignr}Month: ${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
```with the end result at the bottom of my screenshot.

If you have only just installed vnstat you will need to let it make a database before it will give any output.  This is explained when you run vnstat the first time, so try ```
vnstat
``` in terminal and then wait a while for anything to show.  Use ```
vnstat -u -i eth0
```changing the eth0 to whatever you use.  I can't remember if sudo is needed for that command, but think it is.  Try without first, then with sudo if needed.

---

### Post by Arminius on 2011-02-06
when I type in vnstat it returns with ```
 eth0: Not enough data available yet.

``` But my Router is using eth1
tried ```
vnstat eth1
``` and that didn't work


and when I typed ```
vnstat -u -i eth1
```
I got back ```
Error: Unable to read database "/var/lib/vnstat/eth1".
Error: Unable to write database "/var/lib/vnstat/eth1".
```

so yeah that must be where it's going wrong, cause I copied and pasted that code u had for your .conkyrc file and it displayed no stats next to today, week, month.

---

### Post by stinkeye on 2011-02-06
Use
```
sudo vnstat -u -i eth1
```

I don't think you'll see anything until your data reaches 1mb.

---

### Post by Arminius on 2011-02-07
it said it was making a new one to that code ```
sudo vnstat -u -i eth1
```

so does it still keep doing it after I reboot? or do I have to keep punching that code into terminal each time the comp starts?

---

### Post by stinkeye on 2011-02-07
It's now created a database for eht1 and that's all you have to do.
To view the data enter vnstat in the terminal.

---

### Post by Arminius on 2011-02-07
will I be able to reset it to zero once a month?

---

### Post by ajgreeny on 2011-02-07
Yes, just run ```
vnstat -r
```  I think it may need sudo to run as root, but I have never done it, so I'm not sure.  If necessary you could set a cron job to do this once a month.

---

### Post by Arminius on 2011-02-09
is this code working the way it's ment to? full version here ```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
#

# Create own window instead of using desktop (required in nautilus)
# own_window yes
# own_window_type override
background no
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont LiberationSans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5
# maximum_width 300

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 0

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color e5e5e5
color0 66cccc # 'header' color

own_window_colour brown

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 20
gap_y 30

# Rounded corners and 'transparency' w/cairo
lua_load ~/.conky/draw_bg.lua
lua_draw_hook_pre draw_bg

#${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
# ********************************************************************************* #
# stuff after 'TEXT' will be formatted on screen
TEXT





${voffset -65}${goto 178}${font UbuntuTitleBold:size=18}${color brown}${pre_exec lsb_release -r -s}${font}
Kernel: $kernel
Uptime: $uptime
Updates Available: ${execi 1200 aptitude search "~U" | wc -l | tail}

$color0${font UbuntuTitleBold:size=9}CPU${font} ${hr 2}$color
${freq}MHz   Load: ${loadavg}
${font StyleBats:size=15}${font}CPU1: ${color royal blue} ${cpubar cpu1 6,282} ${cpu cpu1}%
${font StyleBats:size=15}${font}${color white}CPU2: ${color royal blue} ${cpubar cpu2 6,282} ${cpu cpu2}%

${color white}NAME${alignr 9}PID     CPU%   MEM%
${top name 1}${alignr 9}${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2}${alignr 9}${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3}${alignr 9}${top pid 3}   ${top cpu 3}    ${top mem 3}

$color0${font UbuntuTitleBold:size=9}MEMORY${font} ${hr 2}$color
RAM: ${color red} ${mem} / ${memmax} ${membar 6,195} (${memperc}%) $color
Swap: ${color red} ${swap}/${swapmax} ${swapbar 6,208} (${swapperc}%) $color

NAME${alignr 9}PID     CPU%   MEM%
${top_mem name 1}${alignr 9}${top_mem pid 1}   ${top_mem cpu 1}    ${top_mem mem 1}
${top_mem name 2}${alignr 9}${top_mem pid 2}   ${top_mem cpu 2}    ${top_mem mem 2}
${top_mem name 3}${alignr 9}${top_mem pid 3}   ${top_mem cpu 3}    ${top_mem mem 3}

$color0${font UbuntuTitleBold:size=9}DISK${font} ${hr 2}$color
Root: ${color light blue} ${fs_used /} ${fs_size /} ${fs_bar 6,204 /} ${fs_used_perc /}% $color
Ext Videos: ${color light blue} ${fs_used /media/Ext Videos} / ${fs_size /media/Ext Videos} ${fs_bar 6,171 /media/Ext Videos} ${fs_used_perc /media/Ext Videos}% $color
Ext VID1.5: ${color light blue} ${fs_used /media/Ext VID1.5} / ${fs_size /media/Ext VID1.5} ${fs_bar 6,172 /media/Ext VID1.5} ${fs_used_perc /media/Ext VID1.5}% $color
Internal Video: ${color light blue} ${fs_used /media/INTERNAL VI} / ${fs_size /media/INTERNAL VI} ${fs_bar 6,155 /media/INTERNAL VI} ${fs_used_perc /media/INTERNAL VI}% $color
Ext Backup1: ${color light blue} ${fs_used /media/Ext Backup1} / ${fs_size /media/Ext Backup1} ${fs_bar 6,162 /media/Ext Backup1} ${fs_used_perc /media/Ext Backup1}% $color
HTC Legend: ${color light blue} ${fs_used /media/900E-A67B} / ${fs_size /media/900E-A67B} ${fs_bar 6,159 /media/900E-A67B} ${fs_used_perc /media/900E-A67B}% $color
${color light blue}${diskiograph 555753 eeeeec}

$color0${font UbuntuTitleBold:size=9}INTERNET TRAFFIC${font} ${hr 2}$color
${color}NETWORK IP:${color}   ${color}${addr eth1}

${color green}DOWN:  ${downspeed eth1}/s         UP:  ${upspeed eth1}/s     
Today:   ${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}                    ${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}  
Week:  ${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${alignr} ${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'} 
Month: ${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${alignr} ${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
```

and code in question is here ```
Today:   ${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}                    ${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}  
Week:  ${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${alignr} ${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'} 
Month: ${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${alignr} ${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
```

isn't displaying anything in week yet which is located at bottom left of photo, even though there's been 2 days worth of downloads and uploads?
so any idea's?

---

### Post by Arminius on 2011-02-12
thanks for everyone's help but this is the right code to achieve what I want.
```
Today:${goto 60}${execi 300 vnstat -i eth1 | grep "today" | awk '{print $2 $3}'}${goto 150} Today:${goto 210}${execi 300 vnstat -i eth1 | grep "today" | awk '{print $5 $6}'}  
Week:${goto 60}${execi 300 vnstat -i eth1 -w | grep "current week" | awk '{print $3 $4}'}${goto 150} Week:${goto 210}${execi 300 vnstat -i eth1 -w | grep "current week" | awk '{print $6 $7}'} 
Month:${goto 60}${execi 300 vnstat -i eth1 -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 150} Month:${goto 210}${execi 300 vnstat -i eth1 -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
```

---

### Post by rvchari on 2011-02-12
[/QUOTE]> **Arminius said:**
> this is the conky code I found, that displays on conky the way I like, problem is everything shows as 0bytes, and stays that way.

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
#

# Create own window instead of using desktop (required in nautilus)
# own_window yes
# own_window_type override
background no
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont LiberationSans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5
# maximum_width 300

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 0

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color e5e5e5
color0 66cccc # 'header' color

own_window_colour brown

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 20
gap_y 30

# Rounded corners and 'transparency' w/cairo
lua_load ~/.conky/draw_bg.lua
lua_draw_hook_pre draw_bg

#${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
# ********************************************************************************* #
# stuff after 'TEXT' will be formatted on screen
TEXT


${voffset -20}Ubuntu: 10.10 "Maverick Meerkat"
Kernel: $kernel
Uptime: $uptime
Updates Available: ${execi 1200 aptitude search "~U" | wc -l | tail}

$color0${font UbuntuTitleBold:size=9}CPU${font} ${hr 2}$color
${freq}MHz   Load: ${loadavg}
${font StyleBats:size=15}${font}CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 6,248}
${font StyleBats:size=15}${font}CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 6,248}

NAME${alignr 9}PID     CPU%   MEM%
${top name 1}${alignr 9}${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2}${alignr 9}${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3}${alignr 9}${top pid 3}   ${top cpu 3}    ${top mem 3}

$color0${font UbuntuTitleBold:size=9}MEMORY${font} ${hr 2}$color
RAM:   $memperc%   ${alignr}${membar 6,220}$color
Swap:  $swapperc%   ${alignr}${swapbar 6,220}$color

NAME${alignr 9}PID     CPU%   MEM%
${top_mem name 1}${alignr 9}${top_mem pid 1}   ${top_mem cpu 1}    ${top_mem mem 1}
${top_mem name 2}${alignr 9}${top_mem pid 2}   ${top_mem cpu 2}    ${top_mem mem 2}
${top_mem name 3}${alignr 9}${top_mem pid 3}   ${top_mem cpu 3}    ${top_mem mem 3}

$color0${font UbuntuTitleBold:size=9}DISK${font} ${hr 2}$color
Root:  ${fs_used_perc /}%   ${alignr}${fs_bar 6,246 /}$color
Ext Videos:  ${fs_used_perc /media/Ext Videos}%   ${alignr}${fs_bar 6,219 /media/Ext Videos}$color
Ext VID1.5:  ${fs_used_perc /media/Ext VID1.5}%   ${alignr}${fs_bar 6,218 /media/Ext VID1.5}$color
Internal Video:  ${fs_used_perc /media/INTERNAL VI}%   ${alignr}${fs_bar 6,203 /media/INTERNAL VI}$color
Ext Backup1:  ${fs_used_perc /media/Ext Backup1}%   ${alignr}${fs_bar 6,210 /media/Ext Backup1}$color
HTC Legend:  ${fs_used_perc /media/900E-A67B}%   ${alignr}${fs_bar 6,218 /media/900E-A67B}$color
${diskiograph 555753 eeeeec}

##################
##   NETWORK    ##
##################
${voffset 6}${font WenQuanYiMicroHei:bold:size=8.75}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}a${font}${color6}${offset 5}Private${offset 3}IP${alignr}${addr eth0}
${font PizzaDudeBullets:size=10}${color2}a${font}${color6}${offset 5}Public${offset 7}IP${alignr}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}T${font}${color6}${offset 5}Down${alignr}${downspeed eth0}
${font PizzaDudeBullets:size=10}${color2}N${font}${color6}${offset 5}Up${alignr}${upspeed eth0}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}T${font}${color6}${offset 5}Downloaded${alignr}${totaldown eth0}
${font PizzaDudeBullets:size=10}${color2}N${font}${color6}${offset 5}Uploaded${alignr}${totalup eth0}
```

with this part being the code I'm most interested in ```
##################
##   NETWORK    ##
##################
${voffset 6}${font WenQuanYiMicroHei:bold:size=8.75}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}a${font}${color6}${offset 5}Private${offset 3}IP${alignr}${addr eth0}
${font PizzaDudeBullets:size=10}${color2}a${font}${color6}${offset 5}Public${offset 7}IP${alignr}${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}T${font}${color6}${offset 5}Down${alignr}${downspeed eth0}
${font PizzaDudeBullets:size=10}${color2}N${font}${color6}${offset 5}Up${alignr}${upspeed eth0}
${voffset 4}${font PizzaDudeBullets:size=10}${color2}T${font}${color6}${offset 5}Downloaded${alignr}${totaldown eth0}
${font PizzaDudeBullets:size=10}${color2}N${font}${color6}${offset 5}Uploaded${alignr}${totalup eth0}
```

so does anyone know what's wrong with it? or can you suggest some code that would work better?



i was looking for tweaking my conky and i found this .
i copied the code and executed it too... is there an option for weatherforecast ? in my prev code, i had it. it is running fine when on direct internet connection, but in office i am connected thru proxy and weatherforecast part says no internet !
any idea to incorporate that into your code ?

i am attaching my screenshot for your ref. notice the left side displaying weather... it says no internet !

another funny display...
in the cpu section, i am usinf a C2D 2267 MHZ, its displaying 800 MHZ, however i notice that the display jumps between 800 and 2267 (the screen shot captured says its 800 !!) is that due to a bug or something else is wrong ?

---

