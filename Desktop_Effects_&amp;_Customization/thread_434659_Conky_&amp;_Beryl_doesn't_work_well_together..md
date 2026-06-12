---
title: "Conky &amp; Beryl doesn't work well together."
date: 2007-05-06
forum: Desktop Effects &amp; Customization
---

### Post by Burbruee on 2007-05-06
Hello.
I'm looking for the answer for these two questions and I couldn't find the answer here when searching.

I'm running Ubuntu Feisty Fawn 7.04 with beryl as my window manager and using XGL rendering.
Just last night I found out about conky and I wanted to put it there on my desktop.

Well here's the problem, when I start conky it doesn't get transparent, it's a black box all around it, and when it updates the old text doesn't get removed from it.
If I turn off Beryl and select Metacity instead all is good, but then I get the black box on kiba-dock and screenlets instead.

My .conkyrc file: ( From the .conkyrc thread. )
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
own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

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

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}

```

Screenshot of conky problem attached.
[http://img340.imageshack.us/my.php?image=screenshot9vu5.png](http://img340.imageshack.us/my.php?image=screenshot9vu5.png)

Output if I run conky from a terminal:
```

burbruee@burbruee-desktop:~$ conky
**Conky: desktop window (120005c) is subwindow of root window (4d)**
Conky: window type - normal
Conky: drawing to created window (3800002)
**Conky: failed to set up double buffer**
Conky: drawing to single buffer
Conky: received SIGINT or SIGTERM to terminate. bye!
burbruee@burbruee-desktop:~$ 

```

What should I do?


Also a second question, what are the sysrequirements to capture desktop video with beryl & kiba-dock etc? I've tried recordmydesktop and vidcap plugin for beryl but it makes my computer reaaaaly slow, feels like it's recording at 0.000001 frames per second. So the outcoming video is unwatchable and I won't be able to show it to my friends. 
AMD Sempron 2 GHz, 1024 MB DDR400, Radeon 9200SE, 250 GB 7200rpm HDD.

Thanks.

---

### Post by hype on 2007-05-18
Hi there, 
to start conky correctly , i use this script (sudo gedit /usr/local/bin/conky.sh)
```
#!/bin/sh
sleep 10
conky&
```
Add conky.sh at startup programs (instead of conky).

Here is my [.conkyrc]("http://hypeuser.free.fr/misc/.conkyrc)

That should work. :)

---

### Post by orb9220 on 2007-05-18
Yours

> # Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

Mine

> # Create own window instead of using desktop (required in nautilus)
#own_window no
#own_window yes
#own_window_type override
#own_window_transparent 1

own_window yes
own_window_transparent yes
own_window_type root
#own_window_hints below sticky undecorated
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

Try adding

own_window_transparent yes

---

### Post by notwen on 2007-05-19
It seems both of your questions have already been answered pretty much, but you may also want to check if you have Load "dbe" under the Module section in your xorg.conf.  Be sure to back it up. =]

---

### Post by Burbruee on 2007-05-19
Ah! The ' Load "dbe" ' part did the trick!
Thank you! :)

---

### Post by notwen on 2007-05-19
Np, glad I could be of service. =]

---

### Post by nevin on 2007-05-26
I'm still having problems with my conky on startup with my beryl session.

I have an xgl session and if i set conky to load on start up, it has the black drop shadow.  so i made the conky.sh script in my /usr/local/bin and added it to the startup programs but i does not start up.  it's supposed to take 10 seconds right?  so i wait, and wait and wait and it doesnt start up.

am i missing something here?

---

### Post by Cresho on 2007-05-26
yes you are you are missing the session part.

go to system->settings->sessions and add on startup command /home/myusername/.conky.sh or the location of your sh file.  this should auto start it up.

a few more things.  to get rid of your jaggy edges, make sure you have anisotrophic filter bumped up a bit and antiliasing.  also, there is a command to force nvidia to load up on start up.  that way, you get no jaggy. 

ps.  your pc spec is too slow for aa and anisotrophic filter.  Other than that, its okay.

---

### Post by randome on 2007-06-07
nvm, it does work ^^

---

