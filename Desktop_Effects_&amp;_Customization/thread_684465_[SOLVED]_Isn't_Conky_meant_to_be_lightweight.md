---
title: "[SOLVED] Isn't Conky meant to be lightweight?"
date: 2008-02-01
forum: Desktop Effects &amp; Customization
---

### Post by NovaAesa on 2008-02-01
I've heard that Conky is meant to be a lightweight application, which sounds good to me. But the thing is, I've recently installed it and it doesn't seem so lightweight. Everything is fine in the memory-department; it's only taking up about 1.5MiB of RAM. However, it seems to be being a bit of a CPU hog. System Monitor is reporting that it is taking up about 15%-25% of my CPU. And this isn't some old CPU either, its a Core 2 Due T7250 (2.0 GHz).

So is Conky actually a lightweight application Maybe I heard incorrectly that it was lightweight? Or are there settings somewhere where I might want to change things a bit to make it use less CPU?

Here's my .conkyrc file:

```
#
# Peter Stace's Conky Configuration
#
# Last edited 01/02/08
#

# set to yes if you want Conky to be forked in the background
background no

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 5.0

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

# Use double buffering to reduce flicker
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Text alignment
alignment top_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 40

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
#uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Sets up the colours
default_color white
default_shade_color black
default_outline_color black

TEXT

SYSTEM
  $nodename - $sysname $kernel on $machine
  Uptime: $uptime
  Load: $loadavg


CPU
  Usage: $cpu% ${cpubar}
  ${cpugraph 0000ff 00ff00}
  Processes: $processes  Running: $running_processes
  

MEMORY
  RAM Usage: $mem/$memmax - $memperc% ${membar}
  Swap Usage: $swap/$swapmax - $swapperc% ${swapbar}


NETWORKING:
 Down: ${downspeed eth0} k/s ${offset 80}Up: ${upspeed eth0} k/s
  ${downspeedgraph eth0 32,150 ff0000 0000ff} ${upspeedgraph eth0 32,150 0000ff ff0000}


FILE SYSTEMS:
  /     ${fs_used /} / ${fs_size /}
  ${fs_bar /}
  /home ${fs_used /home} / ${fs_size /home}
  ${fs_bar /home}
```

---

### Post by NovaAesa on 2008-02-02
Okay I have done a reboot since last night, and it seems to be working well xD It's only using 0.5% now, which is certainly within the range for lightweight IMO.

I have no idea why it did that though. Oh well, it's all better now :)

---

