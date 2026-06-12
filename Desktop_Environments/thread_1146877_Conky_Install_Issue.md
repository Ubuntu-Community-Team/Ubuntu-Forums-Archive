---
title: "Conky Install Issue"
date: 2009-05-03
forum: Desktop Environments
---

### Post by Viligam on 2009-05-03
Hi Everyone,

I followed the directions here [http://www.clububuntu.com/2009/03/installing-conky-in-ubuntu-light-weight.html](http://www.clububuntu.com/2009/03/installing-conky-in-ubuntu-light-weight.html)

I did that to install Conky, however when I try to run it I get an error and I am unsure how to proceed.

```
:~$ conky
Conky: statfs '/home/tmo': No such file or directory
Conky: desktop window (1e000a9) is subwindow of root window (87)
Conky: window type - override
Conky: drawing to created window (0x4200001)
Conky: drawing to double buffer
Conky: statfs '/home/tmo': No such file or directory
Conky: attempting to use more CPUs than you have!
obj->data.cpu_index 2 info.cpu_count 1xxxxxxxxxxxxx:~$
```

---

### Post by Viligam on 2009-05-17
Alright, so I got conky installed, but I seem to have a CPU problem. Here is the code i am using, does anyone have any suggestions to get this working?

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

#  unused text
#  Current:${alignr}${execi 20 /home/tonyt/scripts/.conky_eth2} Mbits/sec
#  hda Temp:${alignr}${execi 1800 /home/tonyt/scripts/.hdtemp}

TEXT
$sysname $kernel
Uptime:$alignr$uptime
${time %A}$alignr${time %F}

Hostname:$alignr$nodename
ath0:$alignr${addr ath0}
Signal:$alignr${linkstatus  ath0}
Current:${alignr}${execi 20 /home/tonyt/scripts/.conky_ath0} Mbits/sec
eth2:$alignr${addr eth2}
Signal:$alignr${linkstatus  eth2}
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

### Post by Viligam on 2009-05-17
Update ... I got it working, but now it seems to be placing it self on the mid-left side, literally right over my application icons and when I go in to try to set it to run on the top right side, it does not move.

Any suggestions? 

Thanks in advance!

---

