---
title: "Conky width and height issue"
date: 2012-03-13
forum: Desktop Environments
---

### Post by EdTheUniqueGeek on 2012-03-13
I am having a problem with getting a wider and higher window in my script. Here is a screenshot of what I have:

[IMG]http://edwardcrosby.com/Commands1.PNG[/IMG]

As you can see some of the lettering is cut off on the right and at the bottom. Here is my config:

```
background yes
update_interval 1

cpu_avg_samples 2
net_avg_samples 2
temperature_unit fahrenheit

double_buffer yes
no_buffers yes
text_buffer_size 2048

gap_x 10
gap_y 10
minimum_size 5 5
maximum_width 300
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_inner_margin 0
border_outer_margin 0
#alignment tr
alignment top_middle

draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no

override_utf8_locale yes
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5
uppercase no

default_color FFFFFF
color1 DDDDDD
color2 AAAAAA
color3 888888
color4 00EE00
color5 EF5A29
color6 5abdf6


TEXT
${font Droid Sans:size=10,weight:bold}${color4}File Commands
${font Droid Sans:size=8}${color}+ ls : directory listing
${font Droid Sans:size=8}${color}+ ls -al : formatted listing with hidden files
${font Droid Sans:size=8}${color}+ cd dir : change directory to dir
${font Droid Sans:size=8}${color}+ cd : change to home
${font Droid Sans:size=8}${color}+ pwd : show current directory
${font Droid Sans:size=8}${color}+ mkdir dir : create a directory dir
${font Droid Sans:size=8}${color}+ rm file : delete file
${font Droid Sans:size=8}${color}+ rm -r dir : delete directory dir
${font Droid Sans:size=8}${color}+ rm -f file : force remove file
${font Droid Sans:size=8}${color}+ rm -rf dir : force remove directory dir *
${font Droid Sans:size=8}${color}+ cp file1 file2 : copy file1 to file2
${font Droid Sans:size=8}${color}+ cp -r dir1 dir2 : copy dir1 to dir2
${font Droid Sans:size=8}${color}+ mv file1 file2 : rename or move file1 to file2

${font Droid Sans:size=10,weight:bold}${color4}Process Management
${font Droid Sans:size=8}${color}+ ps : Show snapshot of processes
${font Droid Sans:size=8}${color}+ top : Show real time processes
${font Droid Sans:size=8}${color}+ kill pid : Kill process with id pid
${font Droid Sans:size=8}${color}+ pkill name : Kill process with name name
${font Droid Sans:size=8}${color}+ killall name : Kill all processes with names beginning name

${font Droid Sans:size=10,weight:bold}${color4}Search Files
${font Droid Sans:size=8}${color}+ grep pattern files : Search for pattern in files
${font Droid Sans:size=8}${color}+ grep -i : Case insens*itive search
${font Droid Sans:size=8}${color}+ grep -r : Recursive search
${font Droid Sans:size=8}${color}+ grep -v : Inverted search
${font Droid Sans:size=8}${color}+ grep -o : Show matched part of file only
${font Droid Sans:size=8}${color}+ find /dir/ -name name* : Find files starting with name in dir
${font Droid Sans:size=8}${color}+ find /dir/ -user name : Find files owned by name in dir
${font Droid Sans:size=8}${color}+ find /dir/ -mmin num : Find files modifed less than num minutes ago in dir
${font Droid Sans:size=8}${color}+ whereis command : Find binary / source / manual for command
${font Droid Sans:size=8}${color}+ locate file : Find file (quick search of system index)

```

What can I change to get a wider and higher window?
Thanks.

---

### Post by ajgreeny on 2012-03-13
The .conkyrc shows alignment top middle, maximum width 300 (pixels) and minimum width 5 5 pixels (not sure about that space) in the forth paragraph showing in your post.

Play around with the maximum width figure and you can get a width that you need.  My conkyrc file shows
```
# Minimum size of text area
minimum_size 280

# Maximum width
maximum_width 280
```for the window sizing, ie the same for min and max size.  I am not sure why the bottom is cut off, however, as I though the height of the window fitted the text lines automatically; it certainly always does on my system.

Here's my whole .conkyrc as it might give you some clues.
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
minimum_size 280

# Maximum width
maximum_width 280

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
gap_y 50

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
${font Trebuchet MS:size=30} ${alignc}${time %k:%M}${font Trebuchet MS:size=11}
${font Trebuchet MS:size=20} ${alignc}${time %a %b %d %Y}${font Trebuchet MS:size=11}
${color #56073D}Name:  ${color #DE0084}$nodename$alignr${color #56073D}Uptime:  ${color #DE0084}$alignr$uptime
${color #56073D}CPU ${cpu cpu1}% ${color #56073D}${cpubar cpu1}
#${color #56073D}CPU ${color #DE0084}${cpu cpu1}% ${color #56073D}${cpubar cpu1}
${color #56073D}${cpugraph 20,280}
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
${color #56073D}${downspeedgraph eth0 20,280}
${color #56073D} Up:${color #DE0084} ${upspeed eth0}/s ${color #56073D}$alignr TOTAL ${color #DE0084}${totalup eth0}
${color #56073D}${upspeedgraph eth0 20,280}
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

### Post by EdTheUniqueGeek on 2012-03-13
I tried playing with the maximum width to as much as 1000 and it still didn't help.
Interestingly enough, I put the config on my laptop and changed it to alignment top_left and all the text is visible.

[img]http://www.edwardcrosby.com/Laptop.png[/img]

```
background yes
#update_interval 1

double_buffer yes
#no_buffers yes
text_buffer_size 3072

gap_x 1
gap_y 1
#minimum_size 500 0
maximum_width 1200
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_margin 0
#border_outer_margin 0
alignment top_left

draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no

override_utf8_locale yes
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5
uppercase no

default_color FFFFFF
color1 DDDDDD
color2 AAAAAA
color3 888888
color4 00EE00
color5 EF5A29
color6 5abdf6


TEXT
###FILE COMMANDS###
${font Droid Sans:size=10,weight:bold}${color4}File Commands
${font Droid Sans:size=8}${color}+ ls : directory listing
${font Droid Sans:size=8}${color}+ ls -al : formatted listing with hidden files
${font Droid Sans:size=8}${color}+ cd dir : change directory to dir
${font Droid Sans:size=8}${color}+ cd : change to home
${font Droid Sans:size=8}${color}+ pwd : show current directory
${font Droid Sans:size=8}${color}+ mkdir dir : create a directory dir
${font Droid Sans:size=8}${color}+ rm file : delete file
${font Droid Sans:size=8}${color}+ rm -r dir : delete directory dir
${font Droid Sans:size=8}${color}+ rm -f file : force remove file
${font Droid Sans:size=8}${color}+ rm -rf dir : force remove directory dir *
${font Droid Sans:size=8}${color}+ cp file1 file2 : copy file1 to file2
${font Droid Sans:size=8}${color}+ cp -r dir1 dir2 : copy dir1 to dir2
${font Droid Sans:size=8}${color}+ mv file1 file2 : rename or move file1 to file2

###PROCESS MANAGEMENT###
${font Droid Sans:size=10,weight:bold}${color4}Process Management
${font Droid Sans:size=8}${color}+ ps : Show snapshot of processes
${font Droid Sans:size=8}${color}+ top : Show real time processes
${font Droid Sans:size=8}${color}+ kill pid : Kill process with id pid
${font Droid Sans:size=8}${color}+ pkill name : Kill process with name name
${font Droid Sans:size=8}${color}+ killall name : Kill all processes with names beginning name

###SEARCH FILES###
${font Droid Sans:size=10,weight:bold}${color4}Search Files
${font Droid Sans:size=8}${color}+ grep pattern files : Search for pattern in files
${font Droid Sans:size=8}${color}+ grep -i : Case insens*itive search
${font Droid Sans:size=8}${color}+ grep -r : Recursive search
${font Droid Sans:size=8}${color}+ grep -v : Inverted search
${font Droid Sans:size=8}${color}+ grep -o : Show matched part of file only
${font Droid Sans:size=8}${color}+ find /dir/ -name name* : Find files starting with name in dir
${font Droid Sans:size=8}${color}+ find /dir/ -user name : Find files owned by name in dir
${font Droid Sans:size=8}${color}+ find /dir/ -mmin num : Find files modifed less than num minutes ago in dir
${font Droid Sans:size=8}${color}+ whereis command : Find binary / source / manual for command
${font Droid Sans:size=8}${color}+ locate file : Find file (quick search of system index)

${font Droid Sans:size=10,weight:bold}${color4}Change DNS IP
${font Droid Sans:size=8}${color}+ cp /etc/resolv.conf /etc/resolv.conf.bak.`date +%m%d%y`
${font Droid Sans:size=8}${color}+ cp /etc/resolv.conf.static /etc/resolv.conf
```

---

### Post by EdTheUniqueGeek on 2012-03-13
I spoke too soon. I added more to the config on my laptop and the bottom is being cut off.

[IMG]http://www.edwardcrosby.com/Laptop1.png[/IMG]

```
background yes
#update_interval 1

double_buffer yes
#no_buffers yes
text_buffer_size 3072

gap_x 1
gap_y 1
#minimum_size 500 0
maximum_width 1200
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_margin 0
#border_outer_margin 0
alignment top_left

draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no

override_utf8_locale yes
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5
uppercase no

default_color FFFFFF
color1 DDDDDD
color2 AAAAAA
color3 888888
color4 00EE00
color5 EF5A29
color6 5abdf6


TEXT
###FILE COMMANDS###
${font Droid Sans:size=10,weight:bold}${color4}File Commands
${font Droid Sans:size=8}${color}+ ls : directory listing
${font Droid Sans:size=8}${color}+ ls -al : formatted listing with hidden files
${font Droid Sans:size=8}${color}+ cd dir : change directory to dir
${font Droid Sans:size=8}${color}+ cd : change to home
${font Droid Sans:size=8}${color}+ pwd : show current directory
${font Droid Sans:size=8}${color}+ mkdir dir : create a directory dir
${font Droid Sans:size=8}${color}+ rm file : delete file
${font Droid Sans:size=8}${color}+ rm -r dir : delete directory dir
${font Droid Sans:size=8}${color}+ rm -f file : force remove file
${font Droid Sans:size=8}${color}+ rm -rf dir : force remove directory dir *
${font Droid Sans:size=8}${color}+ cp file1 file2 : copy file1 to file2
${font Droid Sans:size=8}${color}+ cp -r dir1 dir2 : copy dir1 to dir2
${font Droid Sans:size=8}${color}+ mv file1 file2 : rename or move file1 to file2

###PROCESS MANAGEMENT###
${font Droid Sans:size=10,weight:bold}${color4}Process Management
${font Droid Sans:size=8}${color}+ ps : Show snapshot of processes
${font Droid Sans:size=8}${color}+ top : Show real time processes
${font Droid Sans:size=8}${color}+ kill pid : Kill process with id pid
${font Droid Sans:size=8}${color}+ pkill name : Kill process with name name
${font Droid Sans:size=8}${color}+ killall name : Kill all processes with names beginning name

###SEARCH FILES###
${font Droid Sans:size=10,weight:bold}${color4}Search Files
${font Droid Sans:size=8}${color}+ grep pattern files : Search for pattern in files
${font Droid Sans:size=8}${color}+ grep -i : Case insens*itive search
${font Droid Sans:size=8}${color}+ grep -r : Recursive search
${font Droid Sans:size=8}${color}+ grep -v : Inverted search
${font Droid Sans:size=8}${color}+ grep -o : Show matched part of file only
${font Droid Sans:size=8}${color}+ find /dir/ -name name* : Find files starting with name in dir
${font Droid Sans:size=8}${color}+ find /dir/ -user name : Find files owned by name in dir
${font Droid Sans:size=8}${color}+ find /dir/ -mmin num : Find files modifed less than num minutes ago in dir
${font Droid Sans:size=8}${color}+ find / -name "sophie*.jpg" : Looks for any file on the system that starts with sophie and ends in extension .jpg
${font Droid Sans:size=8}${color}+ find / -name "*.html" : Looks for any file with .html extension
${font Droid Sans:size=8}${color}+ whereis command : Find binary / source / manual for command
${font Droid Sans:size=8}${color}+ locate file : Find file (quick search of system index)

###DNS CHANGE###
${font Droid Sans:size=10,weight:bold}${color4}Change DNS IP
${font Droid Sans:size=8}${color}+ cp /etc/resolv.conf /etc/resolv.conf.bak.`date +%m%d%y`

###NETWORK MAPPING###
${font Droid Sans:size=10,weight:bold}${color4}Open network resource
${font Droid Sans:size=8}${color}+ nautilus smb://ipaddress/folder
```

---

### Post by EdTheUniqueGeek on 2012-03-13
I fixed it and I have no idea how I did it.

[img]http://www.edwardcrosby.com/Laptop2.png[/img]

```
background yes
#update_interval 1

double_buffer yes
#no_buffers yes
text_buffer_size 3082

gap_x 1
gap_y 10
minimum_size 180 500
maximum_width 1200
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_margin 0
#border_inner_margin 0
#border_outer_margin 0
alignment top_left

draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no

override_utf8_locale yes
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5
uppercase no

default_color FFFFFF
color1 DDDDDD
color2 AAAAAA
color3 888888
color4 00EE00
color5 EF5A29
color6 5abdf6


TEXT
###FILE COMMANDS###
${font Droid Sans:size=9,weight:bold}${color4}File Commands
${font Droid Sans:size=7}${color}+ ls : directory listing
${font Droid Sans:size=7}${color}+ ls -al : formatted listing with hidden files
${font Droid Sans:size=7}${color}+ cd dir : change directory to dir
${font Droid Sans:size=7}${color}+ cd : change to home
${font Droid Sans:size=7}${color}+ pwd : show current directory
${font Droid Sans:size=7}${color}+ mkdir dir : create a directory dir
${font Droid Sans:size=7}${color}+ rm file : delete file
${font Droid Sans:size=7}${color}+ rm -r dir : delete directory dir
${font Droid Sans:size=7}${color}+ rm -f file : force remove file
${font Droid Sans:size=7}${color}+ rm -rf dir : force remove directory dir *
${font Droid Sans:size=7}${color}+ cp file1 file2 : copy file1 to file2
${font Droid Sans:size=7}${color}+ cp -r dir1 dir2 : copy dir1 to dir2
${font Droid Sans:size=7}${color}+ mv file1 file2 : rename or move file1 to file2

###PROCESS MANAGEMENT###
${font Droid Sans:size=9,weight:bold}${color4}Process Management
${font Droid Sans:size=7}${color}+ ps : Show snapshot of processes
${font Droid Sans:size=7}${color}+ top : Show real time processes
${font Droid Sans:size=7}${color}+ kill pid : Kill process with id pid
${font Droid Sans:size=7}${color}+ pkill name : Kill process with name name
${font Droid Sans:size=7}${color}+ killall name : Kill all processes with names beginning name

###SEARCH FILES###
${font Droid Sans:size=9,weight:bold}${color4}Search Files
${font Droid Sans:size=7}${color}+ grep pattern files : Search for pattern in files
${font Droid Sans:size=7}${color}+ grep -i : Case insens*itive search
${font Droid Sans:size=7}${color}+ grep -r : Recursive search
${font Droid Sans:size=7}${color}+ grep -v : Inverted search
${font Droid Sans:size=7}${color}+ grep -o : Show matched part of file only
${font Droid Sans:size=7}${color}+ find /dir/ -name name* : Find files starting with name in dir
${font Droid Sans:size=7}${color}+ find /dir/ -user name : Find files owned by name in dir
${font Droid Sans:size=7}${color}+ find /dir/ -mmin num : Find files modifed less than num minutes ago in dir
${font Droid Sans:size=7}${color}+ find / -name "sophie*.jpg" : Looks for any file that starts with sophie and ends in .jpg
${font Droid Sans:size=7}${color}+ find / -name "*.html" : Looks for any file with .html extension
${font Droid Sans:size=7}${color}+ whereis command : Find binary / source / manual for command
${font Droid Sans:size=7}${color}+ locate file : Find file (quick search of system index)

###DNS CHANGE###
${font Droid Sans:size=9,weight:bold}${color4}Change DNS IP
${font Droid Sans:size=7}${color}+ cp /etc/resolv.conf /etc/resolv.conf.bak.`date +%m%d%y`

###NETWORK UTILITIES###
${font Droid Sans:size=9,weight:bold}${color4}Open network resource
${font Droid Sans:size=7}${color}+ nautilus smb://ipaddress/folder

${font Droid Sans:size=9,weight:bold}${color4}NMAP
${font Droid Sans:size=7}${color}+ nmap -sP 192.168.0.1/24 : Scan the network
```

---

### Post by ajgreeny on 2012-03-13
The only difference I can see that would do this is that the "bad" conkyrc shows
> gap_x 1
gap_y 1
[COLOR=Red]#minimum_size 500 0[/COLOR]
maximum_width 1200ie, the minimum size is commented out, and the good one
> gap_x 1
gap_y 10
[COLOR=Red]minimum_size 180 500[/COLOR]
maximum_width 1200so you have added a minimum size for the window.

---

### Post by EdTheUniqueGeek on 2012-03-14
I think I remember playing with that feature, commenting it out and uncommenting and it didn't seem to work...maybe.
Either way, I'm happy it is working now.

---

