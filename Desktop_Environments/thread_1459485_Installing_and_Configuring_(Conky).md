---
title: "Installing and Configuring (Conky)"
date: 2010-04-21
forum: Desktop Environments
---

### Post by Tlawrence on 2010-04-21
Not 100% sure if this is the correct board to be posting, I'm just recently installed Ubuntu on my laptop to try it out. First thing I've noticed is installing software can be pretty confusing. Anything not available through the 'software center' can become messy to install. 

I'll use Conky as an example. I've tried following a few guides, each one seems to get me nowhere. 
[http://ubuntuforums.org/showthread.php?p=6365702](http://ubuntuforums.org/showthread.php?p=6365702)
This is the 'guide' I was following but cannot get much past steps 2 and 3.

---

### Post by wojox on 2010-04-21
Copy and paste this in your .conkyrc file:

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
font arial
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
gap_y 10

# stuff after ‘TEXT’ will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz Load: ${loadavg} Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME PID CPU% MEM%
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM: $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

Root: ${fs_free_perc /}% ${fs_bar 6 /}$color
hda1: ${fs_free_perc /media/hda1}% ${fs_bar 6 /media/hda1}$color
hdb3: ${fs_free_perc /media/hdb3}% ${fs_bar 6 /media/hdb3}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}


```

---

### Post by Tlawrence on 2010-04-21
Really noob question here but, What is my .conkyrc file and where would I find it?

---

### Post by 2hot6ft2 on 2010-04-21
> **Tlawrence said:**
> Really noob question here but, What is my .conkyrc file and where would I find it?
It's a hidden configuration file that will be in your home folder once you copy it there. Going to Places > Home folder and either using Ctrl+h or clicking on View > Show hidden files
will make it visible.

The guide you linked to is old and not updated here are some good ones

Beginners guide
[http://ubuntuforums.org/showthread.php?t=867076](http://ubuntuforums.org/showthread.php?t=867076)

conky screeshots thread
[http://ubuntuforums.org/showthread.php?p=8713982&highlight=weather#post8713982](http://ubuntuforums.org/showthread.php?p=8713982&highlight=weather#post8713982)

conky weather
[http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)

My conky. And welcome to the forum

---

### Post by Tlawrence on 2010-04-22
Alright, thanks for the help.

Now I have a startconky file and its executable at start up. Right now when conky runs it is a plain black box on my desktop, which closes as soon as I click anywhere on the desktop itself.

Does this sound correct?

---

### Post by stinkeye on 2010-04-22
> **Tlawrence said:**
> Alright, thanks for the help.

Now I have a startconky file and its executable at start up. Right now when conky runs it is a plain black box on my desktop, which closes as soon as I click anywhere on the desktop itself.

Does this sound correct?

This is usually caused by a setting in your conky config of
```
own_window_type desktop
```

Try changing it to ```
own_window_type normal
or
own_window_type override

```


For a transparent conky change the line
```
own_window_transparent no
```
to```
own_window_transparent yes
```

Also make sure you have this line in your conky config```
own_window yes
```


As a recent user of Linux you will find things a bit confusing at first,
but persist with it and utilize the forums and it will become easier to use.
Everyone goes through that first learning phase.

---

