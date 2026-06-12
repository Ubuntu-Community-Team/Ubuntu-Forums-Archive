---
title: "[SOLVED] Conky with Compiz?"
date: 2008-12-10
forum: General Help
---

### Post by MattBD on 2008-12-10
I stumbled upon [an articl]("http://maketecheasier.com/how-to-create-a-minimal-and-beautiful-desktop-with-conky/2008/10/30")e earlier today, which I decided to follow as I've never really used Conky before. I was able to set it up fine, and I used Sessions to get it to autostart.

However, I have a bit of a problem. I'm already running Compiz, Emerald and Avant Window Navigator on my desktop. When I log in, I'll often see Conky appear for a moment on the tan background that appears when loggin in, then it will disappear and the wallpaper will appear instead. Conky still appears to be running in the background, but it doesn't appear on screen, so I have to run it again to make it appear on the desktop.

I think it's something to do with Compiz, as Conky appears early on, then has disappeared by the time AWN starts up, since AWN needs Compiz to be running already.

Any ideas for a solution?

---

### Post by m_l17 on 2008-12-10
Have tried to wait until the desktop comes up? If not add sleep for like 5 seconds to the auto start:

```
sleep 5 && conky
```

If 5 seconds doesn't work try a higher number.

You can also create a conky-start.sh:

```
#!/bin/bash
sleep 5 && conky;
```

And use that to start instead the command above and use conky-start.sh in the autostart.

---

### Post by MattBD on 2008-12-10
Strange... I gave that a go and it didn't work, even when I gave it as long as 40 seconds Conky still didn't appear. Nor did it work with the conky-start.sh method. Odd really, because I can see how that should work.
Oh, well. Thanks for your help anyway, m_l17.

---

### Post by m_l17 on 2008-12-10
Maybe try a reboot, that's odd :confused: sorry it didn't work for you. Compiz and Conky play nice on my system.

---

### Post by m_l17 on 2008-12-10
Did you use the .conkyrc from the article? I noticed the person used:

```
own_window_type desktop
```

```
own_window no
```

try

```
own_window_type override
```

```
own_window yes
```

Here is my .conkyrc:

```
### my conky setup for Dell Insipron 531 ###

# XUBUNTU - CONKY- AMD64x2 - VERSION
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
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
#minimum_size 250 5

# Maximum Width
maximum_width 295

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font Terminus -1
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 5

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 5
gap_y 15

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color ffffff}Xubuntu ${hr 2}$color
$sysname $kernel on $machine

${color ffffff}Uptime ${hr 2}$color
${uptime}

${color ffffff}Amd64 X2 4000+ ${hr 2}$color
${freq}MHz $alignr ${cpu cpu0}%  Load ${loadavg}   Temp ${acpitemp}
${cpubar cpu0}
${freq}MHz $alignr ${cpu cpu1}%  Load ${loadavg}   Temp ${acpitemp}
${cpubar cpu1}
${cpugraph 000000 ffffff}
Processes $processes
Running $running_processes

NAME             PID      CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color ffffff}Memory ${hr 2}$color
Mem $alignc $memperc%    $mem / $memmax
${membar 6}$color
Swap $alignc   $swapperc%    $swap / $swapmax  
${swapbar 6}$color

${color ffffff}Hdd ${hr 2}$color
/ $alignc ${fs_free_perc /}%    ${fs_used /}/ ${fs_size /}
${fs_bar 6 /}$color
/home $alignc ${fs_free_perc /home/}%    ${fs_used /home}/ ${fs_size /home}
${fs_bar 6 /home}$color
/data $alignc ${fs_free_perc /data/}%    ${fs_used /data}/ ${fs_size 
/data}
${fs_bar 6 /data}$color
/backup $alignc ${fs_free_perc /backup/}%    ${fs_used /backup}/ ${fs_size /backup}
${fs_bar 6 /backup}$color

${color ffffff}Network ${hr 2}$color
eth0's IP  ${addr eth0}$color

Public IP  ${execi 3600 wget -O - http://whatismyip.org/ | tail}$color

Down $color${downspeed eth0}k/s            Up ${upspeed eth0}k/s
${downspeedgraph eth0 25,140 000000 ffffff}$color ${alignr}${upspeedgraph eth0 25,140 000000 ffffff}$color
Total ${totaldown eth0}          Total ${totalup eth0}
```

---

### Post by MattBD on 2008-12-10
That's cracked it, cheers for that. I've not quite got it how I want it, but I'll have to spend some time tinkering with it to get used to it.

Thanks for your help m_l17!

---

### Post by m_l17 on 2008-12-10
Glad it's working for you. Here are some links.

Home page for conky:

[http://conky.sourceforge.net/]("http://conky.sourceforge.net/")

Documentation:

[http://conky.sourceforge.net/documentation.html]("http://conky.sourceforge.net/documentation.html")

Here is a couple of good guides:

[http://ubuntuforums.org/showthread.php?t=205865]("http://ubuntuforums.org/showthread.php?t=205865")

[http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/]("http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/")

You can get more ideas from here:

[http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")

---

