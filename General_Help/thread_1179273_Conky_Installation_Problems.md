---
title: "Conky Installation Problems"
date: 2009-06-05
forum: General Help
---

### Post by tilerwen on 2009-06-05
Hello,

I am trying to install conky and when I try to run it I get the following errors in the terminal window:


```
terry@terry-desktop:~$ conky
Conky: can't parse X color 'white'
Conky: can't parse X color 'white'
Conky: can't parse X color 'white'
Conky: use_spacer should have an argument of left, right, or none.  'no'
seems to be some form of 'false', so defaulting to none.
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'grey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: can't parse X color 'lightgrey'
Conky: desktop window (e000b0) is subwindow of root window (57)
Conky: window type - normal
Conky: drawing to created window (0x3200002)
Conky: drawing to single buffer

```

I installed it through synaptic package manager. I did add Load "edb" in module section of Xorg.

Anyone have any suggestions? Any help would be appreciated.

---

### Post by Celauran on 2009-06-05
Can you post your .conkyrc? (In code tags, please)

---

### Post by tilerwen on 2009-06-05
Sure, thanks for the reply.

```
# Conky sample configuration

#

# the list of variables has been removed from this file in favour

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

font arial

# Use Xft?

use_xft no

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

update_interval 5.0

# This is the number of times Conky will update before quitting.

# Set to zero to run forever.

total_run_times 0

# Create own window instead of using desktop (required in nautilus)

own_window yes

# If own_window is yes, you may use type normal, desktop or override

own_window_type override

# Use pseudo transparency with own_window?

own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour    here

own_window_colour hotpink

# If own_window is yes, these window manager hints may be used

#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

own_window_hints undecorated,below,sticky

# Use double buffering (reduces flicker, may not work for everyone)

double_buffer yes

# Minimum size of text area

minimum_size 280 5

# Draw shades?

draw_shades no

# Draw outlines?

draw_outline no

# Draw borders around text

draw_borders no

# Draw borders around graphs

draw_graph_borders yes

# Stippled borders?

stippled_borders 8

# border margins

border_margin 4

# border width

border_width 1

# Default colors and also border colors

default_color black

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

gap_y 35

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

# Add spaces to keep things from moving about? This only affects certain objects.

use_spacer no

# Allow each port monitor to track at most this many connections (if 0 or not    set, default is 256)

#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.

#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.

#max_user_text 16384

# variable is given either in format $variable or in ${variable}. Latter

# allows characters right after the variable and must be used in network

# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT

$color $nodename - $sysname $kernel on $machine

$hr

 

 Uptime:${color #606060} $uptime $color - Load:${color #606060} $loadavg

$color CPU Usage:${color #606060} $cpu% ${cpubar}

${color #606060} ${cpugraph 0000ff 00ec00}

$color RAM Usage:${color #606060} $mem/$memmax - $memperc% ${membar}

$color Swap Usage:${color #606060} $swap/$swapmax - $swapperc% ${swapbar}

$color Processes:${color #606060} $processes $color Running:${color #606060}    $running_processes

 

$color$hr

 

 Networking:

 Down:${color #606060} ${downspeed eth0} k/s$color ${offset 80}Up:${color #606060}    ${upspeed eth0} k/s

 ${color #606060}${downspeedgraph eth0 32,150 ff0000 0000ec} ${upspeedgraph eth0    32,150 0000ff ec0000}

$color File systems: / ${color #606060}${fs_used /}/${fs_size /} ${fs_bar /}

 

$color Name PID CPU% MEM%

${color #ec0000} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}

${color #606060} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}

 ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}

 ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

 

$color Mem usage

${color #ec0000} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem    mem 1}

${color #606060} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem    mem 2}

 ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

 

$color$hr

 

 Connections in:${color #606060} ${tcp_portmon 1 32767 count}$color Connections    out:${color #606060} ${tcp_portmon 32768 61000 count}$color Total:${color #606060}    ${tcp_portmon 1 65535 count}

 

$color Inbound Connection ${alignr} Local Service/Port

${color #606060} ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767    lservice 0}

 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}

 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}

 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}

 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}

 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}

 

$color Outbound Connection ${alignr} Remote Service/Port$color

${color #606060} ${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon    32768 61000 rservice 0}

 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice    1}

 ${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice    2}

 ${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice    3}

 ${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice    4}

 ${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice    5}


```

---

### Post by Celauran on 2009-06-05
Aside from having to change "use_spacer no" to "use_spacer none" it worked fine on both my Hardy laptop and Intrepid desktop.

---

### Post by tilerwen on 2009-06-06
Ok, my fault. I was remoted into the computer which was messing with the graphics settings.

---

