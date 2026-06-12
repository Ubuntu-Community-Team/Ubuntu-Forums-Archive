---
title: "Can you help me with my conky please?"
date: 2009-05-06
forum: General Help
---

### Post by tmos22 on 2009-05-06
Hey guys just having a few problems with my conky,i need it edited so that it moves down a bit from the top of the page because i cant see all of the text, also these are the errors im getting when i run it

Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none.
Conky: desktop window (14000a5) is subwindow of root window (13c)
Conky: drawing to desktop window
Conky: drawing to double buffer
Conky: can't open /sys/class/power_supply/AC/uevent: No such file or directory
Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
Conky: can't open /proc/apm: No such file or directory


Could some edit it for me or else just tell me how i can improve it, thanks guys



# Conky configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check [http://conky.sf.net](http://conky.sf.net) for an up-to-date-list.
#
# The additions to this config require curl and xsltproc be installed

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# set to yes if you want Conky to be forked in the background
#background yes

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
#mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
#own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
#own_window_colour black

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Max window size
maximum_width 300

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
stippled_borders 0

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
gap_x 2
gap_y 0
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
gap_y 5

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

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16) 
#min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
#min_port_monitor_connections 256

# none, xmms, bmp, audacious, infopipe (default is none)
#xmms_player none

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color #246eb5}SYSTEM ${hr 2}$color
${time %e %B %G}                   ${alignr}${time %H:%M}
${color #246eb5}Core:$color   ${execi 1000 cat /proc/cpuinfo | grep 'model name' | cut -c 21-31} 2800+ 1.6GHz
${color #246eb5}Host:$color   $nodename 
${color #246eb5}Kernel:$color $kernel 
${color #246eb5}Uptime:$color $uptime
${color #246eb5}POWER ${hr 2}$color
${color #246eb5}Adapter Stat:$color  ${acpiacadapter}    ${color #246eb5}${alignr}Battery Info:$color ${battery}
${color #246eb5}CPU ${hr 2}$color
${color #246eb5}Speed:$color ${freq}MHz  ${color #246eb5}Load:$color ${loadavg} ${color #246eb5}${alignr}CPU Temp:$color ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
${color #246eb5}NAME             PID       CPU%      MEM%$color
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${color #246eb5}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
       $mem of $memmax
Swap:  $swapperc%   ${swapbar 6}$color
       $swap of $swapmax
HDA:   ${fs_free_perc /}%   ${fs_bar 6 /}$color 
${color #246eb5}Total:$color ${fs_used /}   ${color #246eb5}${alignc}Free:$color ${fs_free /}   ${color #246eb5}${alignr}Used:$color ${fs_used /}
${color #246eb5}NETWORK (${addr ppp0}) ${hr 2}$color
${downspeedgraph ppp0 25,140 000000 ff0000} ${alignr}${upspeedgraph ppp0 
25,140 000000 00ff00}$color
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
${color #246eb5}Inbound Connection ${alignr} Local Service/Port$color
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
${color #246eb5}Outbound Connection ${alignr} Remote Service/Port$color
 ${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${color #246eb5}SYSTEM LOGS ${hr 2}$color
${color #246eb5}Messages:$color
${execi 10 /usr/bin/tail -n 4 /var/log/messages | cut -c 27-}
${color #246eb5}Security:$color

---

### Post by tmos22 on 2009-05-06
Anybody?

---

### Post by tmos22 on 2009-05-06
Ok so i have managed to sort out most of the errors except for one which is

Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory

how do i sort this out???????

---

### Post by Uzi304 on 2009-05-06
Change BAT0 to BAT1

---

### Post by tmos22 on 2009-05-06
Sorted now thanks for the advice

---

