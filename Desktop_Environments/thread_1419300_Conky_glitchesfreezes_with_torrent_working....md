---
title: "Conky glitches/freezes with torrent working..."
date: 2010-03-01
forum: Desktop Environments
---

### Post by vickoxy on 2010-03-01
Hi,
i noticed that almost every few seconds my conky just freezes for minute or-two after i add two torrents to download. Actually, it almost doesn´t work/stays freezed almost all the time.
Is there something to fix this?
```
# Use Xft?
use_xft yes
xftfont Andale Mono:size=7
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
minimum_size 160 0
maximum_width 180 0
0 0

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
gap_x 3
gap_y 23

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

# Network Options
if_up_strictness address

TEXT
${font :size=24}${alignc}${time %H:%M:%S}${font}
${voffset 4}${font :size=8}${alignc}${time %A - %d - %B - %Y}${font}
${hr 1}
${voffset 6}${color ffffff}${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color red}'"$DJS"'${color ffffff}'" "/}
${voffset -4}SYSTEM ${hr 1}
kernel: ${alignr}$kernel
uptime: ${alignr}$uptime
${color #3E3E3E}${cpugraph 000000 ffffff}${color}
${voffset -6}cpu: ${cpu}% ${alignr 1} ${alignr}${freq}MHz   ${acpitemp} °C
${voffset 0}hd:  $fs_free_perc%  ${voffset 0}${fs_free /home}/${fs_size /home} ${alignr}${hddtemp /dev/sda localhost 7634} °C
${voffset 0}ram: $memperc% ${alignc} $mem${alignr 7} ${membar 6,50}
${voffset 2}${alignc -40}CPU%	${alignr}MEM%
${voffset 2}${top_mem name 1}${alignr}${top_mem cpu 1}   ${top_mem mem 1}
${voffset 0}${top_mem name 2}${alignr}${top_mem cpu 2}   ${top_mem mem 2}
${voffset 0}${top_mem name 3}${alignr}${top_mem cpu 3}   ${top_mem mem 3}
${voffset 0}${top_mem name 4}${alignr}${top_mem cpu 4}   ${top_mem mem 4}
${voffset 5}upload: ${alignr}${upspeedf eth2} KB/s
${voffset 0}download: ${alignr}${downspeedf eth2} KB/s
```

---

### Post by vickoxy on 2010-03-02
bump

---

### Post by vickoxy on 2010-03-02
UPDATE:
i made another conky distantcalled webspeed. Only to watch up/download-still, this new instance works perfect, but main conky freezes (although i removed up/down)-so does anyone know what is causing this freezing?

```
# Use Xft?
use_xft yes
xftfont Andale Mono:size=7
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
minimum_size 160 0
maximum_width 180 0
0 0

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
gap_x 3
gap_y 23

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

# Network Options
if_up_strictness address

TEXT
${voffset 5}upload: ${alignr}${upspeedf eth2} KB/s
${voffset 0}download: ${alignr}${downspeedf eth2} KB/s
```

---

### Post by vickoxy on 2010-03-02
I tried dozens conkyrc files, changed almost everything-buffersize, positions, gap, font... but still - nothing-keep freezing.
I am sure that download and upload is the issue, although in separate instance that conky works fine.

UPDATE: It has definitely something to do with transmission (torrent)-i deactivated it, and-if i have some other download/high data volume-conky glitches, but seldom, and only for few seconds. But with transmission working it stays almost all the time freeze.

---

### Post by vickoxy on 2010-03-02
Ok- i found what is causing my problem-it is gmail python script for my three accounts:
```
background yes
use_xft yes
xftfont andale mono:size=7
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 170 5
maximum_width 180
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color grey
default_shade_color red
default_outline_color green
alignment top_right
gap_x 3
gap_y 23
no_buffers yes
uppercase no
cpu_avg_samples_2
override_utf8_locale yes
text_buffer_size 2048

TEXT
${font :size=24}${alignc}${time %H:%M:%S}${font}
${voffset 4}${font :size=8}${alignc}${time %A - %d - %B - %Y}${font}
${hr 1}
${voffset 6}${color ffffff}${execpi 600 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color red}'"$DJS"'${color ffffff}'" "/}
${voffset -4}SYSTEM ${hr 1}
kernel: ${alignr}$kernel
uptime: ${alignr}$uptime
${color #3E3E3E}${cpugraph 000000 ffffff}${color}
${voffset -6}cpu: ${cpu}% ${alignr 1} ${alignr}${freq}MHz   ${acpitemp} °C
${voffset 0}hd:  $fs_free_perc%  ${voffset 0}${fs_free /home}/${fs_size /home} ${alignr}${hddtemp /dev/sda localhost 7634} °C
${voffset 0}ram: $memperc% ${alignc} $mem${alignr 7} ${membar 6,50}
${voffset 2}${alignc -40}CPU%	${alignr}MEM%
${voffset 2}${top_mem name 1}${alignr}${top_mem cpu 1}   ${top_mem mem 1}
${voffset 0}${top_mem name 2}${alignr}${top_mem cpu 2}   ${top_mem mem 2}
${voffset 0}${top_mem name 3}${alignr}${top_mem cpu 3}   ${top_mem mem 3}
${voffset 0}${top_mem name 4}${alignr}${top_mem cpu 4}   ${top_mem mem 4}
${voffset 5}upload: ${alignr}${upspeedf eth2} KB/s
${voffset 0}download: ${alignr}${downspeedf eth2} KB/s
[B]${voffset 5}MAIL ${hr 1}
${voffset 0}mail1:${alignr}${execi 45 python ~/.conky/gmail.py}
${voffset 0}mail2:${alignr}${execi 45 python ~/.conky/gmail1.py}
${voffset 0}mmail3:${alignr}${execi 45 python ~/.conky/gmail2.py}[/B]
${voffset 4}WETTER ${hr 1}
${if_up eth2}
${execpi 300 conkyForecast --location=AUXX0025 --template=/home/mini/.conkyForecast.template}
${else}${if_existing /proc/net/route eth2}
${execpi 300 conkyForecast --location=AUXX0025 --template=/home/mini/.conkyForecast.template}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font} Weather Unavailable
${endif}
```

So, is there any fix for this? I would love to have gmail accounts to be seen in conky...
P.S. I made one separat conky only for gmail accounts-both are working just well. No freezing, smooth. But how can i have gmail accounts in my main conky-that is now the question.

SOLVED: thanks to djyoung4:
> try this:
in your terminal:
Code:
gksu gedit /etc/apt/sources.list
add this line to the end of the file:
Code:
deb [http://ppa.launchpad.net/m-buck/ubuntu](http://ppa.launchpad.net/m-buck/ubuntu) hardy main
then back in your terminal type:
Code:
sudo apt-get update
sudo apt-get install conkyemail
then put this in your .conkyrc with appropriate username and password
Code:
${execi 600 conkyEmail --servertype=IMAP --servername=imap.googlemail.com --username=xyz --password=xyz --ssl}
o and make sure you enable the IMAP setting in your Gmail accounts by going to settings-->Forwarding and POP/IMAP

---

### Post by bemental on 2010-09-15
Unfortuntaely, I don't have a Gmail/python script running, only a few conky widgets and a .txt file being displayed via cat... but I still get major freezing (always) when Transmission is running.

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat shows number of connections from your computer and application/PID making it. Kill spyware!
#
# -- Pengo
# 
 
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
 
# Use double buffering (reduces flicker, may not work for everyone)
#double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 2.5
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3
 
# border margins
border_margin 9
 
# border width
border_width 10
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
 
own_window_colour brown
own_window_transparent yes
 
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 10
gap_y 10
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
##$color
##${color orange}SYSTEM ${hr 2}$color
##$nodename $sysname $kernel on $machine
 
${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
 
${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
 
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
 
${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
##${color orange}LOGGING ${hr 2}$color
##${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}
##${color orange}FORTUNE ${hr 2}$color
#${execi 120 fortune -s | fold -w50}

${color orange}TODO ${hr 2}$color
${execi 3 cat /home/bemental/Dropbox/@@todo.txt}

##${color orange}TODO ${hr 2}$color
##${head /home/bemental/gcal.txt 10 20}

```

Thanks for any help that is provided!
Andrew

---

