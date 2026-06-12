---
title: "Conky bash script help needed"
date: 2006-10-19
forum: Desktop Environments
---

### Post by tturrisi on 2006-10-19
I setup Conky just how I want it to look with the desired info displayed.  I use a bash script to grab & print the wifi bit rate:
```
#!/bin/sh
/sbin/iwlist ath0 rate|grep Current|awk -F\= '{print $ath0}'
```

This works fine and displays the current bit rate in Conky. I have Conky setup to also show info for my other wifi device: eth2.  And I have a similar script to display the eth2 bit rate.  The trouble is this:  If eth2 is not connected (meaning I am not currently using that card) then Conky displays nothing (understandable), but the script seems to continuosly run.  This is evident if launch Conky via a shell and the message displayed over & over is: "eth2 no bit-rate information".

What I would like to do is modify each script, the one for ath0 and the one for eth2 using IF-ELSE so that if the interface is down (or not plugged in) then the script is killed and the text to be printed in Conky says something like "not connected".

How do I do this?

Conky Screenshot:
[IMG]http://members.cox.net/tonyt/conky.png[/IMG]

.conkyrc
```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=10

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
minimum_size 160 5

# Maximum width
maximum_width 160

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
#alignment top_left
alignment top_right
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
$sysname $kernel
Uptime:$alignr$uptime
${time %A}$alignr${time %F}

Hostname:$alignr$nodename
ath0:$alignr${addr ath0}
Signal:$alignr${linkstatus  ath0}
${offset -40}${execi 20 /home/tonyt/.conky_ath0 ath0}
eth2:$alignr${addr eth2}
Signal:$alignr${linkstatus  eth2}
${offset -40}${execi 20 /home/tonyt/.conky_eth2 eth2}
eth0:$alignr${addr eth0}
 
RAM: $mem/$memmax ${color lightgray}$membar$color
CPU0 ${cpu cpu1}% ${color lightgray}${cpubar cpu1}$color
CPU1 ${cpu cpu2}% ${color lightgray}${cpubar cpu2}$color

hda3: ${fs_used_perc /}% ${color lightgray}${fs_bar /}$color
hda5: ${fs_used_perc /mnt/FILES}% ${color lightgray}${fs_bar /mnt/FILES/}$color
Swap: $swapperc% ${color lightgray}$swapbar$color

Processes: $processes ${alignr}Running: $running_processes
```

---

