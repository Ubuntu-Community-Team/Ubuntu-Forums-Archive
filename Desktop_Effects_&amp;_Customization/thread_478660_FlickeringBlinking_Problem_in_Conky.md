---
title: "Flickering/Blinking Problem in Conky"
date: 2007-06-19
forum: Desktop Effects &amp; Customization
---

### Post by Kazol on 2007-06-19
I have just installed conky, but it blinks/flickers and has erratic operation when other windows are opened. I checked the double_filtering config option, it was set to "yes."

The information in conky is correct, but displays the error msg "MPD not responding", and "Could not init font path element...", "(WW) NVIDIA(0) WAIT..." I removed the last 2 error msgs by editing the config.

---

### Post by orb9220 on 2007-06-19
This is a known problem when using compiz or beryl. I solved mine with this from my conky file.

> # Create own window instead of using desktop (required in nautilus)
#own_window no
#own_window yes
#own_window_type override
#own_window_transparent 1

own_window yes
own_window_transparent yes
[B]own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager[/B]

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer Yes

Bolded are the key values that worked for me.
Hope it helps.

---

### Post by Kazol on 2007-06-19
I also tried changing other settings, but it still doesn't work. How could you have "root" as the property of own_window_type? It only allows desktop, override, and normal. When I run the app now, it disappears after a few seconds with the terminal window of the app still running.

**_Config:_**
> 
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check [http://conky.sf.net](http://conky.sf.net) for an up-to-date-list.

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
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour hotpink

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

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
#alignment top_right
alignment bottom_left
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

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
$nodename - $sysname $kernel on $machine
$stippled_hr
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU Usage:${color #cc2222} $cpu% ${cpubar}
${color red}${cpugraph 0000ff 00ff00}
${color lightgrey}RAM Usage:$color $mem/$memmax - $memperc% ${membar}
${color lightgrey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$color$stippled_hr
${color lightgrey}Networking:
 Down:${color #8844ee} ${downspeed eth0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed eth0} k/s
${color #0000ff}${downspeedgraph eth0 32,150 ff0000 0000ff} ${color #22ccff}${upspeedgraph eth0 32,150 0000ff ff0000}
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


**_Error Msgs at runtime:_**
> 
Conky: desktop window (100007d) is subwindow of root window (c0)
Conky: drawing to desktop window
Conky: failed to set up double buffer
Conky: drawing to single buffer


---

### Post by NeoLithium on 2007-06-19
Have you loaded 'dbe' in your xorg.conf?

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

gksu gedit /etc/X11/xorg.conf

In "Section Module" add the line
```
        Load    "dbe"
```

Save and restart your xserver :)

---

### Post by orb9220 on 2007-06-19
> How could you have "root" as the property of own_window_type? It only allows desktop, override, and normal. 

No that is the only ones they mention not necessarily the only ones.
and it is not root as filesystem but root as in root x desktop.

---

### Post by Kazol on 2007-06-23
After I enabled the "dbe" option, gdesklets failed to load.

---

