---
title: "transparent conky kills desktop icons"
date: 2008-01-05
forum: Desktop Effects &amp; Customization
---

### Post by richieboy on 2008-01-05
hi.   i have my conky set to transparent and loading 10 seconds after the desktop is done loading.  my desktop loads fine but as soon as conky loads all the icons disappear.  if i move a window, eg:  gedit, over the desktop then the icons reappear until conky updates.

i would like to have my conky transparent (i know, it's faux transparency) and my desktop icons.  this is my rc file:


# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window no
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
Load "dbe"

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color yellow

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color black}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color blue}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color blue}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 

${color blue}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color blue}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}



please someone help.

---

### Post by shirilover on 2008-01-05
If your icons are located on the right side of the screen, then adjusting gap_x to a larger number will move your conky display to the left.

---

### Post by richieboy on 2008-01-05
thanks, but it's not a matter of conky covering the icons.  i have conky top right and all icons on the left.  the icons *_disappear_* from the deskop when conky loads.

---

### Post by unlimitedfin on 2008-01-06
I had the same problem as well but then I followed this guide ([http://ubuntuforums.org/showthread.php?t=205865](http://ubuntuforums.org/showthread.php?t=205865)) to fix it up.

> **seldon77 said:**
> 
For **Compiz / AIGLX users ONLY** please make these changes:
In .conkyrc
```
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```


Apparently you have to start conky as a window when working with compiz otherwise things get funny with the icons. This option will still allow conky to start as a window though still appear as a sticky on the desktop :)

---

### Post by adam.tropics on 2008-01-06
I'd certainly change own_window to yes. Then with window_type, try override, or normal. I had terrible problems with override, but I suspect that was due to my AIGLX being handled by the ati blob driver rather than nvidia. Also, it shouldn't make a jot of differencem but  'own_window_transparent yes' is in there twice.

---

