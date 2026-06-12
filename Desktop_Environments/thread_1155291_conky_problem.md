---
title: "conky problem"
date: 2009-05-10
forum: Desktop Environments
---

### Post by yuki86 on 2009-05-10
hi i have problem with conky.... see my screenshot

[[IMG]http://img134.imageshack.us/img134/9744/conky.th.png[/IMG]](http://img134.imageshack.us/my.php?image=conky.png)

its above all windows... and gnome-panel too

my xorg.conf and .conkyrc

thanks for help

---------------------------------------------

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes
xftfont sans:size=8.5

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 260 5
maximum_width 260

# Draw shades?
draw_shades no

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey


# Text alignment, other possible values are commented
alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 15


TEXT
${color #D28E47}Systém: ${color #ffffff}$nodename Ubuntu
${color #ffffff}$sysname $kernel on $machine
${color #ffffff}Uptime: $uptime
${color white}${hr 1}

${color #D28E47}Monitor systému:
${color #ffffff}CPU: ${color #D28E47}${cpu}%
${color #ffffff}Core: ${color #D28E47}${freq cpu1}MHz

${color #ffffff}RAM: ${color #D28E47}$mem / $memmax - $memperc%

${color #D28E47}Net: ${color #ffffff}(eth0)
${color #ffffff}down: ${color #D28E47}${downspeed eth0} k/s         ${color #ffffff}up: ${color #D28E47}${upspeed eth0} k/s

${color #D28E47}Processes:
${color #FFFFFF}Total: ${color #D28E47}$processes  ${color #ffffff}${alignr}Running:${color #D28E47} $running_processes 

${color #D28E47}Top Processes:
${color #ffffff}Name:               ${alignr}     CPU% 
${color #D28E47}${top name 1}      ${alignr} ${color #D28E47}${top cpu 1}
${color #D28E47}${top name 2}      ${alignr} ${color #D28E47}${top cpu 2}
${color #D28E47}${top name 3}      ${alignr} ${color #D28E47}${top cpu 3}

${texeci 3600 ~/.conky/rates.pl}

${color #D28E47}Disky:
${color #ffffff}root: 
${color #ffffff}${fs_used /} / ${fs_size /} (${fs_free /} ${fs_free_perc /}% free)
${color #D28E47} ${fs_bar /}
${color #ffffff}home:
${color #ffffff}${fs_used /home/jirikrepl} / ${fs_size /home/jirikrepl} (${fs_free /home/jirikrepl} ${fs_free_perc /home/jirikrepl}% free)
${color #D28E47} ${fs_bar /home/jirikrepl}
${color #ffffff}data: 
${color #ffffff}${fs_used /media/DATA} / ${fs_size /media/DATA} (${fs_free /media/DATA} ${fs_free_perc /media/DATA}% free)
${color #D28E47} ${fs_bar /media/DATA}
${color #ffffff}systém win: 
${color #ffffff}${fs_used /media/Windows} / ${fs_size /media/Windows} (${fs_free /media/Windows} ${fs_free_perc /media/Windows}% free)
${color #D28E47} ${fs_bar /media/Windows}

-------------------------------------------------------------


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "ServerFlags"
        Option           "DontZap" "false"
EndSection

---

### Post by heartwarmer on 2009-05-10
try to replace overide with normal "own_window_type normal",
i'm not sure it would work, but there's no harm in trying =)

edit: and if you want to disable the shadow, just add "!conky" 
to shadow windows in window decoration in compiz.

---

### Post by Uzi304 on 2009-05-10
If Conky is starting at start up then instead of starting Conky, start this script at start up 
```
#!/bin/bash
sleep 20;
conky &
```

Conky needs to wait until everything loads first so the script tells Conky to start after a certain amount of time.

---

### Post by frogitts on 2009-05-10
Thanks for that! I've been trying to figure out why conky starts on top of windows, but when I close and restart it, it appears normally. I guess it just has to do with timing, huh? I'll try this, and hopefully it solves my problem too.

---

### Post by yuki86 on 2009-05-11
also thanks

---

### Post by Fallen00Sniper on 2009-06-02
i am using kubuntu 9.04, same difference i would suppose, anyway it can't find my x11 if anyone has any idea how to correct that, it would be nice.

i tried to edit the configure file, but it says the samething, i hope someone knows how to correct it, i also tried in terminal with some of the switches. i assume i do need x11 support to run this.

---

