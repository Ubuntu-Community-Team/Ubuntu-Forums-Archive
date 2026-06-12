---
title: "Conky disappears when closing other programs"
date: 2010-08-30
forum: Desktop Environments
---

### Post by freesitebuilder on 2010-08-30
I'm new to Conky, and have shamelessly copied from the many other conkyrc files posted here!

I have Conky set to start up with a 15 second delay, and it does. But frequently when I close another programme (eg Firefox) Conky disappears. It's still running, and if I log out or reboot I see it for a flash, and it appears OK again when the system starts up.

System info:
Ubuntu 10.04
Kernel 2.6.32-24 generic
Gnome 2.30.2

Processor Intel i5 M520 2.40GHz
Memory 2.9Gib

my conkyrc:

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
own_window_type desktop
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
update_interval 3.0
 
# Minimum size of text area
# minimum_size 250 5
 
# Draw shades?
draw_shades no
 
# Text stuff
draw_outline yes # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
 
# Stippled borders?
stippled_borders 3
 
# border margins
border_inner_margin 9
 
# border width
border_width 10
 
# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

 
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
 
# Gap between borders of screen and text
gap_x 10
gap_y 20
 
# stuff after 'TEXT' will be formatted on screen
 
TEXT
$color
${color #0077ff}SYSTEM ${hr 2}$color
$sysname $kernel $machine - $nodename 
 
${color #0077ff}RAM:${color lightgrey} $mem/$memmax - $memperc% ${alignr}${color #0077ff}${membar 5,110}
${color #0077ff}SWP:${color lightgrey} $swap/$swapmax - $swapperc% ${alignr}${color #0077ff}${swapbar 5,110}

${color #0077ff}Hard Disks:
${color #0077ff}${diskiograph 000000 0077ff}
${color #0077ff} Root ${color lightgrey}${fs_used /}/${fs_size /}${alignr}${color #0077ff}${fs_bar 5,120 /}
${color #0077ff} Home ${color lightgrey}${fs_used /home}/${fs_size /home}${alignr}${color #0077ff}${fs_bar 5,120 /home}

${color #0077ff}CPU Usage	PID	CPU%	MEM%
${color lightgrey} ${top name 1}	${top pid 1}	${top cpu 1}	${top mem 1}
${color #0077ff} ${top name 2}	${top pid 2}	${top cpu 2}	${top mem 2}
${color #0077ff} ${top name 3}	${top pid 3}	${top cpu 3}	${top mem 3}

${freq}MHz Load: ${loadavg}
CPU: ${cpu cpu1}% ${cpubar cpu1}


${color #0077ff}Mem Usage
${color lightgrey} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #0077ff} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #0077ff} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

Memory: ${mem} 
${memperc}% ${membar}

 
${color #0077ff}Network: ${color lightgrey}${addr eth0}

${color #0077ff}Down:${color lightgrey} ${downspeed eth1} k/s $alignr${color #0077ff} Up:${color lightgrey} ${upspeed eth1} k/s
${color #0077ff}${downspeedgraph eth1 27,120 000000 0077ff 180} $alignr${color #0077ff}${upspeedgraph eth1 27,120 000000 0077ff 25}
${color lightgrey}${totaldown eth0}           $alignr${color lightgrey}${totalup eth0}

```

TIA for any info!

---

### Post by Mze on 2010-08-30
Try changing this option "own_window_type desktop" to "own_window_type override" or "own_window_type normal"

Resolved this on my system.

Source: [Conky config settings]("http://conky.sourceforge.net/config_settings.html")

---

### Post by freesitebuilder on 2010-09-19
Changing to override fixed it - thanks! Normal seemed to fix it too, but I could only have it in one position, and it wasn't the position I wanted it in. :)

---

### Post by jcolyn on 2010-09-19
> **freesitebuilder said:**
> Changing to override fixed it - thanks! Normal seemed to fix it too, but I could only have it in one position, and it wasn't the position I wanted it in. :)


You can change window position by making the change to this line.

```
# fiddle with window
 use_spacer right 
```

---

