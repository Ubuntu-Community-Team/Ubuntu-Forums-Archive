---
title: "Conky with openlogos"
date: 2007-12-23
forum: Desktop Effects &amp; Customization
---

### Post by Dark_X on 2007-12-23
I can't get openlogos to work with conky.  This is what I get when I run conky in the terminal:
```
joe@joe-desktop:~$ conky
Conky: desktop window (10000d3) is subwindow of root window (52)
Conky: window type - override
Conky: drawing to created window (4600002)
Conky: drawing to double buffer
Conky: can't load font 'OpenLogos'
Conky: can't load font 'OpenLogos'
Conky: can't load font 'OpenLogos'
Conky: can't load font 'OpenLogos'
Conky: can't load font 'OpenLogos'
Conky: can't load font 'OpenLogos'
Conky: can't load font 'OpenLogos'
```
Here is my conkyrc file:
```
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
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

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
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

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
${color orange}SYSTEM ${hr 2}$color
${font OpenLogos}T u ${font}
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
${top name 5} ${top pid 5}   ${top cpu 5}    ${top mem 5}
${top name 6} ${top pid 6}   ${top cpu 6}    ${top mem 6}
${top name 7} ${top pid 7}   ${top cpu 7}    ${top mem 7}
${top name 8} ${top pid 8}   ${top cpu 8}    ${top mem 8}
${top name 9} ${top pid 9}   ${top cpu 9}    ${top mem 9}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color
sda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color

${color orange}NETWORK (${addr ath0}) ${hr 2}$color
Down: $color${downspeed ath0} k/s ${alignr}Up: ${upspeed ath0} k/s
${downspeedgraph ath0 25,140 000000 ff0000} ${alignr}${upspeedgraph ath0
25,140 000000 00ff00}$color
Total: ${totaldown ath0} ${alignr}Total: ${totalup ath0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}${hr 2}$color
```

---

### Post by erfahren on 2007-12-23
do you have that font installed for system wide use? you may just need it installed for your user (in ~/.fonts )

see: [http://penguinfonts.com/howto/ubuntu.php](http://penguinfonts.com/howto/ubuntu.php)

you also might want to look at this (if you haven't already):
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

---

### Post by Dark_X on 2007-12-23
I have done that already.  I can use them in open office.  I don't know what is wrong with it....
Edit: I found something from 2 years ago, it sounds like the same problem I am having. [http://ubuntuforums.org/showthread.php?t=110794](http://ubuntuforums.org/showthread.php?t=110794)
Edit2: I just compiled it and it still won't work, but it says this and doesn't repeat "Conky: can't load font 'openlogos'".
```
joe@joe-desktop:~$ conky
Conky: desktop window (a000c1) is subwindow of root window (52)
Conky: window type - override
Conky: drawing to created window (4c00002)
Conky: drawing to double buffer
Conky: can't load font 'openlogos'

```

---

### Post by Freaky_Llama on 2008-02-18
Old thread resurrection, but I was having the same issue with Conky and this is the only true thread I could find via Google.

In your .conkyrc file, especially the one listed above, you have to change xft from no to yes. 

what you have above:

```
# fiddle with window
use_spacer yes
use_xft no
```

you need to change to:

```
# fiddle with window
use_spacer yes
use_xft yes
```

I did this on my system, and now any of the system fonts work. I used purisa in my test. Prior to this fix, it was giving me the same error. I even recompiled conky to 1.4.9 (from 1.4.7).
EDIT: I continue to use my "font" setting, not having to change it. Attached here is my current .conkyrc: (Just as **Tristam Green **pointed out below, check my rc file, it shows the syntax of file sizing from within the rc.)

```

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background no
own_window_colour grey
own_window_transparent yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 5.0

# Minimum size of text area
minimum_size 300 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font gentium:size=10
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$nodename Ubuntu $sysname  Uptime: $UPTIME
$color$stippled_hr
CPU: ${freq}MHz  Util: ${cpu}%
$cpubar

${top name 1}
|-${top pid 1}(pid)  ${top cpu 1}(cpu)
${top name 2}
|-${top pid 2}(pid)  ${top cpu 2}(cpu)
${top name 3}
|-${top pid 3}(pid)  ${top cpu 3}(cpu)
$color$stippled_hr
RAM: $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

Root: ${fs_used_perc /}% ${fs_bar 6 /}$color
Home: ${fs_used_perc /home}% ${fs_bar 6 /home}$color
$color$stippled_hr
IP: ${addr eth0} Total: ${totaldown eth0} Down ${totalup eth0} Up

Down: ${downspeed eth0} k/s ${offset 110}Up: ${upspeed eth0} k/s
$color$stippled_hr
${execi 30 tail -n4 /var/log/messages | fold -w75}
```

---

### Post by Tristam Green on 2008-02-18
> **Freaky_Llama said:**
> Old thread resurrection, but I was having the same issue with Conky and this is the only true thread I could find via Google.

In your .conkyrc file, especially the one listed above, you have to change xft from no to yes. 

what you have above:

```
# fiddle with window
use_spacer yes
use_xft no
```

you need to change to:

```
# fiddle with window
use_spacer yes
use_xft yes
```


This;  also it might help to specify a size.

${font OpenLogos:size=13}  is a fairly decent size to get the GNOME and Ubuntu logos legible.

---

