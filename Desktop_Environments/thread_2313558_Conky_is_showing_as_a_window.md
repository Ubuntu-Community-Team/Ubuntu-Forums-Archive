---
title: "Conky is showing as a window"
date: 2016-02-13
forum: Desktop Environments
---

### Post by asmcriminal on 2016-02-13
I have been searching for a solution since last night and I can not find one. My issue is that Conky windows are showing as a normal window. Meaning they have a maximize, minimize and a normal icon on top. How can I remove this? I am on running Ubuntu Mate. As you can see per the attached image it has the resizing options.

---

### Post by deadflowr on 2016-02-13
Post the .conkyrc configuration file, please.

---

### Post by asmcriminal on 2016-02-13
> **deadflowr said:**
> Post the .conkyrc configuration file, please.

here, I actually have this issue with a lot of the conky windows. 

```
#==============================================================================
#                               conkyrc_seamod
# Date    : 05/02/2012
# Author  : SeaJey
# Version : v0.1
# License : Distributed under the terms of GNU GPL version 2 or later
# 
# This version is a modification of conkyrc_lunatico wich is modification of conkyrc_orange
# 
# conkyrc_orange:    [http://gnome-look.org/content/show.php?content=137503&forumpage=0](http://gnome-look.org/content/show.php?content=137503&forumpage=0)
# conkyrc_lunatico:  [http://gnome-look.org/content/show.php?content=142884](http://gnome-look.org/content/show.php?content=142884)
#==============================================================================


background yes
update_interval 1


cpu_avg_samples 1
net_avg_samples 2
temperature_unit celsius


double_buffer yes
no_buffers yes
text_buffer_size 2048


gap_x 40
gap_y 70
minimum_size 300 900
maximum_width 350


own_window yes
own_window_type normal
own_window_transparent yes
own_window_argb_visual yes
own_window_argb_visual yes
own_window_colour 000000
own_window_argb_value 0
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below


border_inner_margin 0
border_outer_margin 0
alignment top_right




draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no


override_utf8_locale yes
use_xft yes
xftfont caviar dreams:size=10
xftalpha 0.5
uppercase no


# Defining colors
default_color FFFFFF
# Shades of Gray
color1 DDDDDD
color2 AAAAAA
color3 888888
# Orange
color4 EF5A29
# Green
color5 77B753


# Loading lua script for drawning rings
lua_load ./seamod_rings.lua
lua_draw_hook_post main


## System information using conky capabilities


# Header with base system info
own_window_argb_value 0
own_window_colour 000000
TEXT
${font Ubuntu:size=10,weight:bold}${color4}SYSTEM ${hr 2}
${offset 15}${font Ubuntu:size=10,weight:normal}${color1}$sysname $kernel
${offset 15}${font Ubuntu:size=10,weight:normal}${color1}$nodename
${offset 15}${font Ubuntu:size=10,weight:normal}${color1}Uptime: $uptime


# Showing CPU Graph
${voffset 20}
${offset 120}${cpugraph 40,183 666666 666666}${voffset -25}
${offset 90}${font Ubuntu:size=10,weight:bold}${color5}CPU
# Showing TOP 5 CPU-consumers
${offset 105}${font Ubuntu:size=10,weight:normal}${color4}${top name 1}${alignr}${top cpu 1}%
${offset 105}${font Ubuntu:size=10,weight:normal}${color1}${top name 2}${alignr}${top cpu 2}%
${offset 105}${font Ubuntu:size=10,weight:normal}${color2}${top name 3}${alignr}${top cpu 3}%
${offset 105}${font Ubuntu:size=10,weight:normal}${color3}${top name 4}${alignr}${top cpu 4}%
${offset 105}${font Ubuntu:size=10,weight:normal}${color3}${top name 5}${alignr}${top cpu 5}%


#Showing memory part with TOP 5
${voffset 40}
${offset 90}${font Ubuntu:size=10,weight:bold}${color5}MEM
${offset 105}${font Ubuntu:size=10,weight:normal}${color4}${top_mem name 1}${alignr}${top_mem mem 1}%
${offset 105}${font Ubuntu:size=10,weight:normal}${color1}${top_mem name 2}${alignr}${top_mem mem 2}%
${offset 105}${font Ubuntu:size=10,weight:normal}${color2}${top_mem name 3}${alignr}${top_mem mem 3}%
${offset 105}${font Ubuntu:size=10,weight:normal}${color3}${top_mem name 4}${alignr}${top_mem mem 4}%
${offset 105}${font Ubuntu:size=10,weight:normal}${color3}${top_mem name 4}${alignr}${top_mem mem 5}%


# Showing disk partitions: root, home and Data
${voffset 28}
${offset 90}${font Ubuntu:size=10,weight:bold}${color5}DISKS
${offset 120}${diskiograph 33,183 666666 666666}${voffset -30}
${voffset 20}
${offset 15}${font Ubuntu:size=9,weight:bold}${color1}Free: ${font Ubuntu:size=9,weight:normal}${fs_free /}${alignr}${font Ubuntu:size=9,weight:bold}Used: ${font Ubuntu:size=9,weight:normal}${fs_used /}
${offset 15}${font Ubuntu:size=9,weight:bold}${color1}Free: ${font Ubuntu:size=9,weight:normal}${fs_free /home}${alignr}${font Ubuntu:size=9,weight:bold}Used: ${font Ubuntu:size=9,weight:normal}${fs_used /home}
${offset 15}${font Ubuntu:size=9,weight:bold}${color1}Free: ${font Ubuntu:size=9,weight:normal}${fs_free /media/Data}${alignr}${font Ubuntu:size=9,weight:bold}Used: ${font Ubuntu:size=9,weight:normal}${fs_used /media/Data}


# Network data (my desktop have only LAN). ETHERNET ring is mostly useless but looks pretty, main info is in the graphs
${voffset 43}
${offset 90}${font Ubuntu:size=10,weight:bold}${color5}ETHERNET
${voffset 40}             
${offset 15}${color1}${font Ubuntu:size=9,weight:bold}Up: ${alignr}${font Ubuntu:size=9,weight:normal}$color2${upspeed eth0} / ${totalup}
${offset 15}${upspeedgraph eth0 40,285 4B1B0C FF5C2B 100 -l}
${offset 15}${color1}${font Ubuntu:size=9,weight:bold}Down: ${alignr}${font Ubuntu:size=9,weight:normal}$color2${downspeed eth0} / ${totaldown}
${offset 15}${downspeedgraph eth0 40,285 324D23 77B753 100 -l}


${color4}${hr 2}
```

---

### Post by ajgreeny on 2016-02-13
I can not see any obvious treason from the conky configuration file for your conky window to show with all window decorations as it does.

How do you start conky?  If it's in the startup applications list for your mate session using simply the command ```
conky
``` it is possible that it is starting before the DE is running fully, and therefore is not starting as it should.

To test this out, stop all conky instances running with command ```
killall conky
``` and then start it again with command ```
conky
``` If it now runs as you expect you will need to edit the startup command you are using in the startup applications list to ```
conky -p 20
``` to pause it starting for 20 seconds.

---

### Post by deadflowr on 2016-02-13
Try changing 
```
own_window yes
```
to 
```
own_window no
```
See if that helps.

---

### Post by asmcriminal on 2016-02-13
> **deadflowr said:**
> Try changing 
```
own_window yes
```
to 
```
own_window no
```
See if that helps.

I apologize that was not the .conkyrc file. I posted the conky_seamod file for the widget. What you recommended did help but now the desktop icons are hidden. In regards to the .conckyrc file I checked my home directory and type ctr+h to show hidden files I do not see it. It appears to be missing, I even did a search with the terminal and I can not find the .conkyrc file.

---

### Post by asmcriminal on 2016-02-13
> **ajgreeny said:**
> I can not see any obvious treason from the conky configuration file for your conky window to show with all window decorations as it does.

How do you start conky? If it's in the startup applications list for your mate session using simply the command ```
conky
``` it is possible that it is starting before the DE is running fully, and therefore is not starting as it should.

To test this out, stop all conky instances running with command ```
killall conky
``` and then start it again with command ```
conky
``` If it now runs as you expect you will need to edit the startup command you are using in the startup applications list to ```
conky -p 20
``` to pause it starting for 20 seconds.

I am starting the widget with "conky manager". If I type conky directly into the terminal the conky loads fine.  I do not believe it is in the startup applications. I have not set up any startups for it. I just run the

---

### Post by asmcriminal on 2016-02-13
I found the back up of the conky file. I renamed it .conkyrc and put it in my home folder. 

```
-- vim: ts=4 sw=4 noet ai cindent syntax=lua--[[
Conky, a system monitor, based on torsmo


Any original torsmo code is licensed under the BSD license


All code written since the fork of torsmo is licensed under the GPL


Please see COPYING for details


Copyright (c) 2004, Hannu Saransaari and Lauri Hakkarainen
Copyright (c) 2005-2012 Brenden Matthews, Philip Kovacs, et. al. (see AUTHORS)
All rights reserved.


This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.


This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.
You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
]]


conky.config = {
    alignment = 'top_left',
    background = false,
    border_width = 1,
    cpu_avg_samples = 2,
	default_color = 'white',
    default_outline_color = 'white',
    default_shade_color = 'white',
    draw_borders = false,
    draw_graph_borders = true,
    draw_outline = false,
    draw_shades = false,
    use_xft = true,
    font = 'DejaVu Sans Mono:size=12',
    gap_x = 5,
    gap_y = 60,
    minimum_height = 5,
	minimum_width = 5,
    net_avg_samples = 2,
    no_buffers = true,
    out_to_console = false,
    out_to_stderr = false,
    extra_newline = false,
    own_window = true,
    own_window_class = 'Conky',
    own_window_type = 'desktop',
    stippled_borders = 0,
    update_interval = 1.0,
    uppercase = false,
    use_spacer = 'none',
    show_graph_scale = false,
    show_graph_range = false
}


conky.text = [[
${scroll 16 $nodename - $sysname $kernel on $machine | }
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
${color grey}Networking:
Up:$color ${upspeed eth0} ${color grey} - Down:$color ${downspeed eth0}
$hr
${color grey}Name              PID   CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
]]
```

---

### Post by deadflowr on 2016-02-14
> **asmcriminal said:**
> I am starting the widget with "conky manager". If I type conky directly into the terminal the conky loads fine.  I do not believe it is in the startup applications. I have not set up any startups for it. I just run the

Sorry, I know nothing about how conky manager operates.

Also, did you mean to let the post end with such suspense?  :popcorn:

---

### Post by asmcriminal on 2016-02-14
> **deadflowr said:**
> Sorry, I know nothing about how conky manager operates.

Also, did you mean to let the post end with such suspense? :popcorn:

ha oops, it meant to say "i just open it with conky manager." If it is not common practice to use the conky manager can you point me in the direction of how to use conky without the manager?

---

### Post by ajgreeny on 2016-02-14
Just like deadflowr, I do not know nor use conky-manager, and have never seen it in use, so can not help you with that.

I start conky automatically at session start with the command ```
conky -p 20
``` in the list, as I suggested to you above.

I do not recognise the config file you have posted as a conky configuration either and I have shown my .conkyrc file below for you to look at and see what you could copy from it to give the output on desktop that you want.
```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Ubuntu:size=11

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
own_window_type desktop

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
draw_shades yes

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
# default_shade_color red
# default_outline_color green

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 25
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 4

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen

TEXT
${color #FF0000}${font Ubuntu:size=20} ${alignc}${time %A %b %d %Y}
${font Ubuntu:size=40} ${alignc}${time %k:%M}${font Ubuntu:size=16}
${font Ubuntu:size=12}${color #FFFFFF}$nodename${alignr}Uptime:  $uptime
Kernel:${alignr}${exec uname -r # | cut -c 15-31}${font Ubuntu:size=11}

${color #FFFFFF}CPU1	${cpu cpu0}% ${color #FFA500}${cpubar cpu0}${color #FFFFFF}
CPU2	${cpu cpu1}% ${color #FFA500}${cpubar cpu1}${color #FFFFFF}
CPU3	${cpu cpu2}% ${color #FFA500}${cpubar cpu2}${color #FFFFFF}
CPU4	${cpu cpu3}% ${color #FFA500}${cpubar cpu3}
${cpugraph 20,320}${color #FFFFFF}
#Process CPU & MEM Usage${hr 2}        
Processes $alignr CPU%   MEM%   PID
 ${top name 1}  $alignr ${top cpu 1}  ${top mem 1}  ${top pid 1}
 ${top name 2}  $alignr ${top cpu 2}  ${top mem 1}  ${top pid 2}
# ${top name 3}  $alignr ${top cpu 3}  ${top mem 1}  ${top pid 3}
# ${top name 4}  $alignr ${top cpu 4}  ${top mem 1}  ${top pid 4}

Root$alignr ${fs_used /}/${fs_size /}
${fs_used_perc /}% ${color #FFA500}${fs_bar /}${color #FFFFFF}
Home$alignr ${fs_used /home}/${fs_size /home}
${fs_used_perc /home}% ${color #FFA500}${fs_bar /home}${color #FFFFFF}

RAM Used:$alignr$mem of $memmax = $memperc%
Swap:${alignr}$swapperc%     $swap of $swapmax

NETWORK IP: $alignr eth0 -  ${addr eth0}
DOWN: ${downspeed eth0}/s$alignr UP: ${upspeed eth0}/s
${color #FFA500}${downspeedgraph eth0 40,158}$alignr${upspeedgraph eth0 40,158}${color #FFFFFF}
#TOTAL ${totaldown eth0}$alignr TOTAL ${totalup eth0}
#NETWORK IP: $alignr eth0 -  ${addr eth0}
#DOWN: ${downspeed eth0}/s $alignr TOTAL ${totaldown eth0}
#${downspeedgraph eth0 20,320}
#UP: ${upspeed eth0}/s $alignr TOTAL ${totalup eth0}
#${upspeedgraph eth0 20,320}
#
# To make hddtemp run as user use command "sudo chmod u+s /usr/sbin/hddtemp"
# To make vnstat run as user use command "sudo chmod u+s /usr/bin/vnstat"
# "${execi 60 vnstat" updates figures every 60 seconds.
     DOWN:							${alignr}UP:     
TODAY: ${execi 60 vnstat | grep "today" | awk '{print $2 $3}'}${alignr}TODAY: ${execi 60 vnstat | grep "today" | awk '{print $5 $6}'}
Week:  ${execi 60 vnstat -w | grep "current week" | awk '{print $3 $4}'}${alignr}Week:  ${execi 60 vnstat -w | grep "current week" | awk '{print $6 $7}'}
Month: ${execi 60 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${alignr}Month: ${execi 60 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}

#${font Ubuntu:size=12}Temperatures: Degrees C${font Ubuntu:size=11}
CPU Temperature:                         ${alignr}${acpitemp} C
#Disk Temperature: hddtemp:              ${alignr}${execi 60 hddtemp /dev/sda | cut -c 30-32} C
Disk Temperature:                     ${alignr}${execi 60 udisks --show-info /dev/sda | grep temp | cut -c 52-53} C

```
Some of this will need editing, of course, to fit your system, but this may give you some clues.

My conky output is shown in the attachment.

---

### Post by CantankRus on 2016-02-14
> **asmcriminal said:**
> ha oops, it meant to say "i just open it with conky manager." If it is not common practice to use the conky manager can you point me in the direction of how to use conky without the manager?
Conky Manager(CM) is just an easy way to run different conky configs.
CM looks for conky configs in **~/.conky** ....which is a hidden folder in your home directory.
ctrl+h in your file browser to show hidden.

The included conky configs have been adapted to work with CM in that they may use relative paths to run other scripts.

eg in the seamod conky you posted, a [COLOR="#FF0000"]relative path[/COLOR] is used to run the lua script...
```
# Loading lua script for drawning rings
lua_load [COLOR="#FF0000"]./seamod_rings.lua[/COLOR]
lua_draw_hook_post main
```

What this means is you have to first change directory to where the **seamod_rings.lua** file is before running the seamod conky config.
eg
```
cd "/home/glen/.conky/Conky Seamod" **&&** conky -c "/home/glen/.conky/Conky Seamod/conky_seamod"
```

---

### Post by asmcriminal on 2016-02-14
Thanks guys, I read the replies and I will get back to you later I am really busy at the moment.

---

### Post by asmcriminal on 2016-02-16
> **CantankRus said:**
> Conky Manager(CM) is just an easy way to run different conky configs.
CM looks for conky configs in **~/.conky** ....which is a hidden folder in your home directory.
ctrl+h in your file browser to show hidden.

The included conky configs have been adapted to work with CM in that they may use relative paths to run other scripts.

eg in the seamod conky you posted, a [COLOR=#FF0000]relative path[/COLOR] is used to run the lua script...
```
# Loading lua script for drawning rings
lua_load [COLOR=#FF0000]./seamod_rings.lua[/COLOR]
lua_draw_hook_post main
```

What this means is you have to first change directory to where the **seamod_rings.lua** file is before running the seamod conky config.
eg
```
cd "/home/glen/.conky/Conky Seamod" **&&** conky -c "/home/glen/.conky/Conky Seamod/conky_seamod"
```


At this point I am a bit confused. If I was not using ConkyManager I would run my .conkyrc  instead correct?  I am just wondering if I can just copy and paste what ajgreeny posted above into my conkyrc file and run it? (obviously with necessary changes).

---

### Post by ajgreeny on 2016-02-16
> **asmcriminal said:**
> At this point I am a bit confused. If I was not using ConkyManager I would run my .conkyrc  instead correct?  I am just wondering if I can just copy and paste what ajgreeny posted above into my conkyrc file and run it? (obviously with necessary changes).
You can certainly try it though some of the entries I have will probably show errors, or may stop conky running at all, or perhaps just leave empty spaces in the output.  It needs to be a hidden file in your home by default called .conkyrc (note the . at start of name).  You do not run the .conkyrc file itself as it is merely the default configuration file for conky.  You can use any file as the configuration, as long as it has that same layout and syntax format, by using command **conky -c /path/to/filename** and in this way you can run simultaneous multi-instances of conky with different config files.

Start it from terminal with command **conky** and see what happens.  A lot will depend on your hardware, the programs you have installed (I have **vnstat** set to run as user instead of root as it normally runs), and I have a quad-core cpu showing at the top of my output, but you will not do any harm to anything if you try and it does not work; just close the terminal and conky should close.

---

### Post by RockDoctor on 2016-02-18
FWIW, here is my ~/.conkyrc file. Screenshot of the output attached.

```

conky.config={
    alignment = 'bottom_right',
    background = false,
    border_width = 1,
    color0 = 'green',
    color1 = 'white',
    cpu_avg_samples = 2,
    default_color = 'yellow',
    default_outline_color = 'black',
    default_shade_color = 'black',
    draw_borders = false,
    draw_graph_borders = true,
    draw_outline = true,
    draw_shades = false,
    double_buffer = true,
    use_xft = true,
    font = 'Liberation Sans Bold:size=8',
    gap_x = 25,
    gap_y = 625,
    minimum_height = 5,
    minimum_width = 5,
    net_avg_samples = 2,
    no_buffers = true,
    out_to_console = false,
    out_to_stderr = false,

    own_window = true,
    own_window_type = normal,
    own_window_argb_visual = true,
    own_window_transparent = true,
    own_window_hints = 'undecorated, skip_taskbar',

    stippled_borders = 0,
    text_buffer_size = 1024,
    update_interval = 10.0,
    uppercase = false,
    use_spacer = none,
    show_graph_scale = false,
    show_graph_range = false,
}

conky.text = [[
${execpi 300 /home/a/Projects/conky/metar_109.sh}
]]

```

---

### Post by CantankRus on 2016-02-18
> **asmcriminal said:**
> At this point I am a bit confused. If I was not using ConkyManager I would run my .conkyrc  instead correct?  I am just wondering if I can just copy and paste what ajgreeny posted above into my conkyrc file and run it? (obviously with necessary changes).
When you run "conky" it will look for and use a config file located @ **~/.conkyrc**
If this file does not exist it will load the default config from **/etc/conky/conky.conf**

Alternatively you can run any config with the **-c** option.
eg ```
conky -c /path/to/config
```
When using the "**-c**" option , a conky config can be named whatever you like and located wherever
you like. 

Some conky configs may use additional scripts and you must check you have the scripts
and the paths in the config actually point to the location where you saved them.
You must also check you have any additional fonts being used.

If you only want to run 1 instance of conky, yes you can copy a config you like to **~/.conkyrc**
which will then be used when you run "conky"

---

