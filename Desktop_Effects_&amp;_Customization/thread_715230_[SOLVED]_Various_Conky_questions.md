---
title: "[SOLVED] Various Conky questions"
date: 2008-03-04
forum: Desktop Effects &amp; Customization
---

### Post by sci-fi guy on 2008-03-04
I would appreciate any help I can get configuring Conky.

Question 1: Can I merge two graphs (ie like having the graph of cpu0 merged with cpu1)
Question 2: Can I have a graph move from left to right rather than right to left?
Question 3: Is there a way to have a running total of MBs downloaded over a certain period of time (the past day, month...) Preferably a method that doesn't start counting from 0 again after a reboot.
Question 4: A battery charge monitor.
Question 5: My IP address(es)
Question 6: My kernel version
Question 7: I would like to filter some of the programs in the CPU utilization and Mem usage sections so that they don't show up (ie  Nautilus and gnome-panel are consistently at the top of the Mem usage list. I would rather those spaces go to other programs.)

My .conkyrc:```
# Conky sample configuration
#
# the list of variables has been removed from this file in favor
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval .75

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent no

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour black

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline yes

# Draw borders around text
draw_borders yes

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

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

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# Timing interval for music player thread, e.g. mpd, audacious
#music_player_interval (update_interval is default)

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
$nodename - $sysname $kernel on $machine
$stippled_hr
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU Frequency: ${freq cpu1} MHz
${color lightgrey}CPU1 Usage:${color #cc2222} ${cpu cpu1}% ${cpubar cpu1}
${color lightgrey}CPU2 Usage:${color #cc2222} ${cpu cpu2}% ${cpubar cpu2}
${color red}${cpugraph cpu0 20,150 0000ff 00ff00} ${color red}${cpugraph cpu1 20,150 0000ff 00ff00}
${color lightgrey}RAM Usage:$color $mem/$memmax - $memperc% ${membar}
${color lightgrey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$color$stippled_hr
${color lightgrey}Networking:
 Down:${color #8844ee} ${downspeed eth0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed eth0} k/s
${color #0000ff}${downspeedgraph eth0 25,150 ff0000 0000ff} ${color #22ccff}${upspeedgraph eth0 25,150 0000ff ff0000}
${color #0000ff}${downspeedgraph eth1 25,150 ff0000 0000ff} ${color #22ccff}${upspeedgraph eth1 25,150 0000ff ff0000}
${color lightgrey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar /}
${color #88aadd}MPD: ${alignc}$mpd_artist - $mpd_title
${color #88aadd}$mpd_bar
${color #88aadd}${alignc}$mpd_status
${color}Name              PID     CPU%   MEM%
${color #ddaa00} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color}Mem usage
${color #ddaa00} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color lightgrey} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color lightgrey} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
$stippled_hr
${color #ddaa00}Port(s)${alignr}#Connections   
$color Inbound: ${tcp_portmon 1 32767 count}  Outbound: ${tcp_portmon 32768 61000 count}${alignr}ALL: ${tcp_portmon 1 65535 count}
${color #ddaa00}Inbound Connection ${alignr} Local Service/Port$color
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
${color #ddaa00}Outbound Connection ${alignr} Remote Service/Port$color
 ${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
 ${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
 ${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
 ${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
 ${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}
```Thank You!

---

### Post by cammin on 2008-03-05
1: I don't think there is.
You can try using a negative offset on a 2nd graph to try and overlay the two. I don't know if it will work, though.
${color #0000ff}${downspeedgraph eth0 25,150 ff0000 0000ff}${offset -150}${downspeedgraph eth1 25,150 ff0000 0000ff}
It will most likely just mess things up. You can also try voffset and add the graph to the next line, but If offset doesn't work, this probably won't, either.

2: I don't think so.
3: you could probably make an external script that does that and have conky call it, but it doesn't have that feature.

4: take your pick
battery
battery bar
battery_percent
battery_time
you need to include the battery number inside the curly braces. Most likely 0

There are specific variables for Macs and Thinkpads too, check the man page for them if you need them.

5: ${addr} specify which interface you need the IP off of. Probably eth0
6: $kernel , it's in your .conky.rc file right now.
**$nodename - $sysname $kernel on $machine**

7: again, you can probably script it, but it's not an included feature.

The man page lists all the conky variables.

---

### Post by sci-fi guy on 2008-03-05
Thanks!

Running total of what works as I test them:

Overlaid graphs (somewhat working. graph 1 is hidden behind graph 2 when it is lesser in value)
Kernel version: it was/is hidden by my panel. can I move conky down a few pixels?
IP addresses: working, although now I am curious if I can have my internet IP address displayed.

---

### Post by cammin on 2008-03-06
# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12


change gap_y to at least the height of your panel.

---

