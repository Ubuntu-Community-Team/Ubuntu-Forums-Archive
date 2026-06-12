---
title: "Conky Guide"
date: 2012-11-30
forum: Desktop Environments
---

### Post by jackal_79 on 2012-11-30
Hi, i need some help in installing and running conky.I have tried googling and also going through this forum. But many of them are confusing. i would like to have a guide in installing conky. i would like to run following conky if possible. please help

[http://desktopspotting.com/wp-content/uploads/2011/05/crunchbang_conky_by_quickdraw-590x368.jpg](http://desktopspotting.com/wp-content/uploads/2011/05/crunchbang_conky_by_quickdraw-590x368.jpg)

---

### Post by ajgreeny on 2012-11-30
Installing it is the same as anything else; use synaptic, software-centre, apt-get install, or whatever you normally use.

The config file ~/.conkyrc is a bit more difficult to give you full details here, but here is my .conkyrc which has some of the same things as you want, so you may be able to figure out at least some of the edits you need to get what you want..
```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=11

# Text alpha when using Xft
xftalpha 0.9

# Update interval in seconds
update_interval 2.0

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
minimum_size 320

# Maximum width
maximum_width 320

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

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
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 30
gap_y 40

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen

TEXT
${font Trebuchet MS:size=24} ${alignc}${time %k:%M}${font Trebuchet MS:size=20}  ${alignr}${time %a %b %d %Y}${font Trebuchet MS:size=11}
${color #56073D}Name:  ${color #DE0084}$nodename$alignr${color #56073D}Uptime:  ${color #DE0084}$alignr$uptime
${color #56073D}CPU ${cpu cpu1}% ${color #56073D}${cpubar cpu1}
#${color #56073D}CPU ${color #DE0084}${cpu cpu1}% ${color #56073D}${cpubar cpu1}
${color #56073D}${cpugraph 20,320}
#${color #56073D}Process CPU & MEM Usage${hr 2}        
Processes $alignr CPU%   MEM%   PID
${color #56073D} ${top name 1} ${color #DE0084} $alignr ${top cpu 1}  ${top mem 1}  ${top pid 1}
${color #56073D} ${top name 2} ${color #DE0084} $alignr ${top cpu 2}  ${top mem 1}  ${top pid 2}
#${color #56073D} ${top name 3} ${color #DE0084} $alignr ${top cpu 3}  ${top mem 1}  ${top pid 3}
#${color #56073D} ${top name 4} ${color #DE0084} $alignr ${top cpu 4}  ${top mem 1}  ${top pid 4}

${color #56073D}sda1$alignr ${color #DE0084}${fs_used /}/${fs_size /}
${color #56073D} Root ${color #DE0084}${fs_used_perc /}% ${color #56073D}${fs_bar /}

${color #56073D}sda2$alignr ${color #DE0084}${fs_used /home}/${fs_size /home}
${color #56073D} Home ${color #DE0084}${fs_used_perc /home}% ${color #56073D}${fs_bar /home}

${color #56073D}RAM Used:$alignr${color #DE0084}$mem of $memmax ${color #DE0084}= ${color #DE0084}$memperc%
${color #56073D}Swap:${alignr}${color #DE0084}$swapperc%     $swap of $swapmax

${color #56073D}NETWORK IP:${color #DE0084} $alignr eth0 -  ${color #DE0084}${addr eth0}
${color #56073D}DOWN:${color #DE0084} ${downspeed eth0}/s ${color #56073D}$alignr TOTAL ${color #DE0084}${totaldown eth0}
${color #56073D}${downspeedgraph eth0 20,320}
${color #56073D} Up:${color #DE0084} ${upspeed eth0}/s ${color #56073D}$alignr TOTAL ${color #DE0084}${totalup eth0}
${color #56073D}${upspeedgraph eth0 20,320}
#
# To make hddtemp run as user use command "sudo chmod u+s /usr/sbin/hddtemp"
# To make vnstat run as user use command "sudo chmod u+s /usr/bin/vnstat"
#
            DOWN:                    $alignr UP:        
${color #56073D}Today: ${color #DE0084}${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${color #56073D}${alignr}Today: ${color #DE0084}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}
${color #56073D}Week:  ${color #DE0084}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${color #56073D}${alignr}Week:  ${color #DE0084}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'}
${color #56073D}Month: ${color #DE0084}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${color #56073D}${alignr}Month: ${color #DE0084}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}

${color #56073D}${font Trebuchet MS:size=12}Drive Temp: Degrees C${font Trebuchet MS:size=11}
     ${execi 60 hddtemp /dev/sda | cut -c 6-28} C
     ${execi 60 hddtemp /dev/sdb | cut -c 6-28} C
```

---

### Post by DuckHook on 2012-11-30
You might find this site useful:

[http://wiki.conky.cc/index.php?title=Conky_Wiki](http://wiki.conky.cc/index.php?title=Conky_Wiki)

---

### Post by jackal_79 on 2012-12-01
> **ajgreeny said:**
> Installing it is the same as anything else; use synaptic, software-centre, apt-get install, or whatever you normally use.

The config file ~/.conkyrc is a bit more difficult to give you full details here, but here is my .conkyrc which has some of the same things as you want, so you may be able to figure out at least some of the edits you need to get what you want..

Thanks for the file.It's working. But not all parameters are shown.
But when i try other configs like the one i mentioned in post above either it's not at all displaying or it's there when booting up, but disappears after i do something on my system.

Below is the file i tried can someone take a look?
================================================================
# .conkyrc by fabsh <fabsh@lamerk.org>
# Based on ideas and code from the CunchBang Linux forums at [http://crunchbanglinux.org](http://crunchbanglinux.org)
# v. 1.0

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 4

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

own_window yes
own_window_transparent yes
#own_window_type override
own_window_type desktop
#own_window_type normal #use this if you want a nice shadow to appear around conky

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

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
default_color black
#default_shade_color black
#default_outline_color grey
own_window_colour grey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 8

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

# Add spaces to keep things from moving about? This only affects certain objects.
use_spacer none

TEXT
SYSTEM ${hr 2}
${alignc 24}${font Arial Black:size=14}${nodename}${font}
${alignc -8}HP Pavilion dv2500nr
${voffset 2}${font Arial Black:style=Bold:size=12}#!${font} CrunchBang Linux ${alignr}08.10.01
${font OpenLogos:size=16}u${font} Kernel: ${alignr}${kernel}
${font StyleBats:size=16}A${font} CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font} CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${font StyleBats:size=16}g${font} RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font} SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font Webdings:size=16}~${font} Battery: ${battery_percent BAT0}% ${alignr}${battery_bar 8,60 BAT0}
${font StyleBats:size=16}q${font} Uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 19}${font Arial Black:size=18}${time %H:%M}${font}
${voffset 2}${alignc}${time %A, %d %B %Y}

WEATHER ${hr 2}
${if_existing /proc/net/route eth1}
${voffset -8}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=WF}${font}
${voffset -52}${font ConkyWeather:size=40}y${font}${voffset -38}${font Trebuchet MS:size=26}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=HT}${font}


${voffset 0}${font}Barometer Tendency: ${alignr}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=BD}
${voffset 0}Humidity: ${alignr}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=HM}
${voffset 0}${font}Wind Speed: ${alignr}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --hideunits --datatype=WS} km/h ${execi 600 /usr/bin/conkyForecast --location=USOH0189 --hideunits --datatype=WD}
${voffset 0}${font}Wind Gusts: ${alignr}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=WG}
${voffset 0}Daylight: ${alignr}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=SR} - ${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=SS}

${font Trebuchet MS:size=12}${execi 600 /usr/bin/conkyForecast --location=CAXX0126 --datatype=MP}
${voffset -30}${alignr 42}${font MoonPhases:size=24}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=MF}${font}
${else}${if_existing /proc/net/route eth1}
${voffset -8}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=WF}${font}
${voffset -52}${font Weather:size=40}y${font} ${voffset -38}${font Arial Black:size=26}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=HT}${font}


${voffset 0}Humidity: ${alignr}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=HM}
${voffset 0}${font}Wind Speed: ${alignr}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --hideunits --datatype=WS} km/h ${execi 600 /usr/bin/conkyForecast --location=USOH0189 --hideunits --datatype=WD}
${voffset 0}${font}Wind Gusts: ${alignr}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=WG}
${voffset 0}Daylight: ${alignr}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=SR} - ${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=SS}

${font Trebuchet MS:size=12}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=MP}
${voffset -30}${alignr 42}${font MoonPhases:size=28}${execi 600 /usr/bin/conkyForecast --location=USOH0189 --datatype=MF}${font}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font} Weather Unavailable
${endif}
${voffset -10}HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font} ${voffset -5}Root:
${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}

NETWORK ${hr 2}
${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font} Up: ${upspeed eth1}${alignr}${upspeedgraph eth1 8,60 black black}
${voffset 4}${font PizzaDude Bullets:size=14}U${font} Down: ${downspeed eth1}${alignr}${downspeedgraph eth1 8,60 black black}
${voffset 4}${font PizzaDude Bullets:size=14}N${font} Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font} Download: ${alignr}${totaldown eth1}
${endif}
==============================================================

---

### Post by stinkeye on 2012-12-01
The first thing to try is using **own_window_type normal**. Change this section of your config...
```
own_window yes
own_window_transparent yes
#own_window_type override
own_window_type desktop
#own_window_type normal #use this if you want a nice shadow to appear around conky
```

to
```
own_window yes
own_window_transparent yes
#own_window_type override
#own_window_type desktop
own_window_type normal #use this if you want a nice shadow to appear around conkyconky
```

Also your config is using kaivalagi's conkyForecast scripts, which  I'm not sure
if they still work.
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=869328")

The network section is using eth1 where you may be using eth0 or wlan0(wireless).
To find your network interface run in the terminal **ifconfig** or for wireless **iwconfig**


Notice this section in your config.
```
WEATHER ${hr 2}
${if_existing /proc/net/route [COLOR="magenta"]eth1[/COLOR]}
```
It will only run if eth1 exists so it needs to be set to [COLOR="Magenta"]your network interface[/COLOR] along with other instances of eth1 in the config.

Running **conky** in terminal will show errors in the config.

This thread is a great resource for conky.
[**_[COLOR="darkred"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=2120")

---

### Post by jackal_79 on 2012-12-01
> **stinkeye said:**
> The first thing to try is using **own_window_type normal**. Change this section of your config...
```
own_window yes
own_window_transparent yes
#own_window_type override
own_window_type desktop
#own_window_type normal #use this if you want a nice shadow to appear around conky
```

to
```
own_window yes
own_window_transparent yes
#own_window_type override
#own_window_type desktop
own_window_type normal #use this if you want a nice shadow to appear around conkyconky
```

Also your config is using kaivalagi's conkyForecast scripts, which  I'm not sure
if they still work.
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=869328")

The network section is using eth1 where you may be using eth0 or wlan0(wireless).
To find your network interface run in the terminal **ifconfig** or for wireless **iwconfig**


Notice this section in your config.
```
WEATHER ${hr 2}
${if_existing /proc/net/route [COLOR="magenta"]eth1[/COLOR]}
```
It will only run if eth1 exists so it needs to be set to [COLOR="Magenta"]your network interface[/COLOR]

Running **conky** in terminal will show errors in the config.

This thread is a great resource for conky.
[**_[COLOR="darkred"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=2120")

It's working now. Network is also working.But weather is not working(Screenshot Attached). Also this script was made for a laptop i guess. How do i remove laptop model and battery data? Also how do i make the weather work? It is only showing only one hdd partition how do i make all partitions and disks visible including removable drives?
                 I also want to add CPU, GPU RAM Temp.How do i do that?

---

### Post by jackal_79 on 2012-12-01
Again my conky has become invisible. Now my desktop is plain again. Someone please suggest.

---

### Post by stinkeye on 2012-12-01
> **jackal_79 said:**
> It's working now. Network is also working.But weather is not working(Screenshot Attached). Also this script was made for a laptop i guess. How do i remove laptop model and battery data? Also how do i make the weather work? It is only showing only one hdd partition how do i make all partitions and disks visible including removable drives?
                 I also want to add CPU, GPU RAM Temp.How do i do that?
You have to look at the config.
eg the first part of the config below "TEXT" shows the **laptop model** and **CrunchBang Linux** are hard coded.
```
TEXT
 SYSTEM ${hr 2}
 ${alignc 24}${font Arial Black:size=14}${nodename}${font}
 ${alignc -8}[COLOR="Red"]HP Pavilion dv2500nr[/COLOR]
 ${voffset 2}${font Arial Black:style=Bold:size=12}#!${font} [COLOR="red"]CrunchBang Linux[/COLOR] ${alignr}08.10.01
```

Best way to learn is go to the previous conky thread link and look at pics of conkys that show what you want and download the config to see how it's done.
Download any configs you want, give them a descriptive name and save somwhere like ~/conky.
Load any of the configs with...
```
conky -c [COLOR="DimGray"]*/path/to/config*[/COLOR]
```

In terminal, for an explanation of settings and variables... 
```
man conky
```

---

### Post by stinkeye on 2012-12-01
> **jackal_79 said:**
> Again my conky has become invisible. Now my desktop is plain again. Someone please suggest.
With some window managers 
```
own_window_type **desktop**
```
causes conky to disappear when clicking the desktop.

Use...
```
own_window_type normal
```

If that doesn't work run conky in terminal for possible errors.

---

### Post by paramvir on 2012-12-02
> **jackal_79 said:**
> Again my conky has become invisible. Now my desktop is plain again. Someone please suggest.

I am the author of conkywx - a bash weather script for conky - using wunderground for data.

You will need to get your hands dirty at some point and that is by far the best way to get a handle on conky. It can be very addictive.

You can have a look at the blog [http://foreverquest.blogspot.in/2012/11/conky-weather-program-in-bash-script.html](http://foreverquest.blogspot.in/2012/11/conky-weather-program-in-bash-script.html)

There is also a help wiki and a vinDSL thread - lot of action - [http://ubuntuforums.org/showthread.php?t=1771033&page=72](http://ubuntuforums.org/showthread.php?t=1771033&page=72)

Vin is using conkywx for his conky desktop scripts.

You will need to remove the weather section and add new information - it is really quite easy once you start fiddling around :D

cheers

Paramvir

---

### Post by jackal_79 on 2012-12-02
> **stinkeye said:**
> With some window managers 
```
own_window_type **desktop**
```
causes conky to disappear when clicking the desktop.

Use...
```
own_window_type normal
```

If that doesn't work run conky in terminal for possible errors.

On running Conky on terminal, i got this:
=====================================
jackal@Treadstone:~$ conky
Conky: /home/jackal/.conkyrc: 47: no such configuration: 'border_margin'
Conky: can't open '/sys/class/thermal/thermal_zone0/temp': No such file or directory
Conky: one or more $endif's are missing
Conky: desktop window (1200045) is subwindow of root window (b6)
Conky: window type - override
Conky: drawing to created window (0x3800001)
Conky: drawing to double buffer
sh: 1: /usr/bin/conkyForecast: not found
sh: 1: /usr/bin/conkyForecast: not found
sh: 1: /usr/bin/conkyForecast: not found
sh: 1: /usr/bin/conkyForecast: not found
sh: 1: /usr/bin/conkyForecast: not found
sh: 1: /usr/bin/conkyForecast: not found
sh: 1: /usr/bin/conkyForecast: not found
sh: 1: /usr/bin/conkyForecast: not found
sh: 1: /usr/bin/conkyForecast: not found
sh: 1: /usr/bin/conkyForecast: not found
sh: 1: /usr/bin/conkyForecast: not found
^CConky: received SIGINT or SIGTERM to terminate. bye!
jackal@Treadstone:~$ 

=========================================================

what does it mean?

---

### Post by DuckHook on 2012-12-02
> **paramvir said:**
> You will need to get your hands dirty at some point...

+1 @paramvir

Conky isn't meant to be used by just following instructions. If you don't understand what is really going on in the script, there is a limit to what help can be derived from a forum. There are apps that are designed to be just end-user apps (libreoffice, browsers), and then there are apps like Conky that are designed to be scripting and fiddling-around type apps. A good way to start is to load a simple Conky script and try to parse what each of its components are doing. Good links given by @paramvir

---

### Post by jackal_79 on 2012-12-02
> **DuckHook said:**
> +1 @paramvir

Conky isn't meant to be used by just following instructions. If you don't understand what is really going on in the script, there is a limit to what help can be derived from a forum. There are apps that are designed to be just end-user apps (libreoffice, browsers), and then there are apps like Conky that are designed to be scripting and fiddling-around type apps. A good way to start is to load a simple Conky script and try to parse what each of its components are doing. Good links given by @paramvir

Understood! and have been doing that ever since.But this conky becoming invisible is the most troubling thing.Please help to stop this.Will take it up from there!

---

### Post by DuckHook on 2012-12-03
> **jackal_79 said:**
> ...this conky becoming invisible is the most troubling thing.

I can sympathize. Because scripting is a form of programming, even small errors will render the script inoperative. In your latest code sample, you are still setting *own_window_type* to *override*. As previous posters have all instructed, you must try this at *normal*. The placement of the "#" (comment marks) may be confusing you. Comment out the *override* line and uncomment the *normal* line.

> Will take it up from there!

My own experience with Conky was to start with the much simpler default script. Only after I got that working properly did I start adding components one by one. In this way, I learned what each component did and was able to isolate which addition broke the script. Trying to decipher a pretty but complex script from the outset is overwhelming and you may want to approach it the opposite way.

As I have posted earlier, the Conky wiki is very good. It has step-by-step instructions for creating the default script and recommends the same methodology of learning/making/testing small discrete changes thereafter.

Good luck. Once you get the Conky fundamentals mastered, Conky is both fun and stupidly addictive.

---

