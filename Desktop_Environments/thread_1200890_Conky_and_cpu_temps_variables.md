---
title: "Conky and cpu temps variables"
date: 2009-06-30
forum: Desktop Environments
---

### Post by Jeffa on 2009-06-30
Hello all, 

I've been giving conky a try but I've hit a roadblock. I'd like to have it display cpu temps. I'm running a C2D. I've installed conky, curl, lm-sensors and hddtemp. I've run sensors-detect and run modprobe w83627ehf and  coretemp. Here is the output from running sensors:
```
jeff@jeff-desktop:~$ sensors
w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.28 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +12.09 V  (min =  +8.45 V, max =  +5.33 V)   ALARM
AVCC:        +3.31 V  (min =  +1.44 V, max =  +0.26 V)   ALARM
3VCC:        +3.31 V  (min =  +2.05 V, max =  +1.28 V)   ALARM
in4:         +1.39 V  (min =  +1.03 V, max =  +0.59 V)   ALARM
in5:         +1.55 V  (min =  +1.68 V, max =  +1.02 V)   ALARM
in6:         +4.38 V  (min =  +1.79 V, max =  +1.36 V)   ALARM
VSB:         +3.28 V  (min =  +0.00 V, max =  +3.33 V)   
VBAT:        +3.23 V  (min =  +2.38 V, max =  +0.83 V)   ALARM
Case Fan:   1562 RPM  (min =    0 RPM, div = 8)  ALARM
CPU Fan:    1383 RPM  (min = 168750 RPM, div = 8)  ALARM
Aux Fan:    1591 RPM  (min = 2163 RPM, div = 8)  ALARM
fan4:       1534 RPM  (min =  387 RPM, div = 16)
fan5:       1467 RPM  (min = 3515 RPM, div = 8)  ALARM
Sys Temp:    +53.0°C  (high =  +0.0°C, hyst = +80.0°C)  sensor = thermistor
CPU Temp:    +29.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
AUX Temp:    +98.0°C  (high = +80.0°C, hyst = +75.0°C)  ALARM  sensor = thermistor
cpu0_vid:   +1.325 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +57.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +58.0°C  (high = +78.0°C, crit = +100.0°C) 
```

it's obviously reading something. Now the question is, how do I get conky to display this information? Here is my conkyrc file:

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
double_buffer yes
 
# fiddle with window
use_spacer right

# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048
 
# Update interval in seconds
update_interval 1.0
 
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
border_width 20
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color 99ccff
 
own_window_colour brown
own_window_transparent yes
 
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 40
gap_y 80
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
${color 3366cc}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
 
${color 3366cc}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
${cpubar cpu1 15}
${cpubar cpu2 15}
CPU 1 Temp ${execi 10 sensors | grep "Core 0" | cut -d "+" -f2 | cut -c1-6}C
CPU 2 Temp ${execi 10 sensors | grep "Core 1" | cut -d "+" -f2 | cut -c1-6}C
${cpugraph cpu1 99ccff 3366cc}
${cpugraph cpu2 99ccff 3366cc}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
 
${color 3366cc}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
 
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda1:  ${fs_free_perc /media/sdc1}%   ${fs_bar 6 /media/sdc1}$color
 
${color 3366cc}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}
${color 3366cc}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}

Section "Module"
        Load    "dbe"
EndSection
```

and included is a screenshot:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=119489&stc=1&d=1246387100[/IMG]

I found the following lines in another thread:

```
CPU 1 Temp ${execi 10 sensors | grep "Core 0" | cut -d "+" -f2 | cut -c1-6}C
CPU 2 Temp ${execi 10 sensors | grep "Core 1" | cut -d "+" -f2 | cut -c1-6}C
```

but I don't realy understand what they are doing. Are the temps displayed from those lines from either coretemp or w83627dhg? Why isn't the $acpitemp variable displaying accurate temps? (it's only displaying 0 degrees) Do I need to use coretemp or w83627dhg to display the other temps? (like systemp and aux temp) why is cpu temp listed as 29 degrees in the w83627dhg-isa-0290 section, but the individual core temps are listd as 57 and 58 degrees in the coretemp-isa-0000 section? 

Your help in this matter is greatly appreciated.

---

