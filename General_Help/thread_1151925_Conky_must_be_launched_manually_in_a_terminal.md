---
title: "Conky must be launched manually in a terminal???"
date: 2009-05-07
forum: General Help
---

### Post by jjrev on 2009-05-07
Hi there, 

So I'm running 8.04.2 (x86_64) and the only way I can get conky to start is to launch it manually in a terminal.  This is rather strange to me.  

I've tried adding an entry via the "Sessions" menu, but that doesn't seem to work.

I've also tried to make a cronjob that does something like this:
```

killall conky; conky

```
But that only kills conky and doesn't launch a new one...:confused:

Here is my .conkyrc
```

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.

# fork to background
background yes

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_title my_conky
own_window_transparent yes
#own_window_type desktop
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer left
use_xft yes

# Update interval in seconds
update_interval 1
total_run_times 0

# Minimum size of text area
# minimum_size 250 5

# Maximum width of text area
maximum_width 400

# Draw shades?
draw_shades no

# Text stuff
draw_outline yes # amplifies text if yes
draw_borders no
xftfont mono-10
uppercase yes # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
#default_color grey
#default_color grey90
default_color white

#own_window_colour brown
#own_window_transparent yes

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
${color orange}SKULL TRAIL SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine
UPTIME: ${uptime}

${color orange}INTEL XEON CPU (8 Cores @ ${freq_g}GHz) ${hr 2}$color 
CPU1: ${cpubar cpu1}
CPU2: ${cpubar cpu2}
CPU3: ${cpubar cpu3}
CPU4: ${cpubar cpu4}
CPU5: ${cpubar cpu5}
CPU6: ${cpubar cpu6}
CPU7: ${cpubar cpu7}
CPU8: ${cpubar cpu8}
${cpugraph cpu0 25 FF0000 FF0000}

${color orange}PROCESSES ${hr 2}$color
NAME              ${alignr}PID   CPU%   MEM%
${top name 1} ${alignr}${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${alignr}${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${alignr}${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${alignr}${top pid 4} ${top cpu 4} ${top mem 4}
${top name 5} ${alignr}${top pid 5} ${top cpu 5} ${top mem 5}
${top name 6} ${alignr}${top pid 6} ${top cpu 6} ${top mem 6}
${top name 7} ${alignr}${top pid 7} ${top cpu 7} ${top mem 7}
${top name 8} ${alignr}${top pid 8} ${top cpu 8} ${top mem 8}

${color orange}MEMORY / DISK ${hr 2}$color
RAM: $memperc% ${membar 6}$color
SWP: $swapperc% ${swapbar 6}$color

SDA1: ${fs_used_perc /}% ${fs_bar /}$color
SDB1: ${fs_used_perc /media/samba_disk}% ${fs_bar /media/samba_disk}$color
SDC1: ${fs_used_perc /media/share}% ${fs_bar /media/share}$color
SDD1: ${fs_used_perc /mnt/.backup_main}% ${fs_bar /mnt/.backup_main}$color
SDD2: ${fs_used_perc /mnt/.backup_storage}% ${fs_bar /mnt/.backup_storage}$color

${color orange}NETWORK (${addr br0}) ${hr 2}$color
Dn: $color${downspeedf eth0}k/s ${alignr}Total: ${totaldown eth0}
${downspeedgraph eth0 25 0000FF 0000FF} 
Up: ${upspeedf eth0}k/s ${alignr}Total: ${totalup eth0}
${upspeedgraph eth0 25 00FF00 00FF00}$color

${color orange}LAST BACKUP LOG (eSATA) ${hr 2}$color
${tail /home/<user>/backup.log 3}

```

Any help is greatly appreciated!

---

### Post by Joeb454 on 2009-05-07
You could add an entry to your applications menu that runs conky. That should allow you to run conky graphically.

It should work when added to sessions though, how did you add it?

---

### Post by ubuser_7 on 2009-05-07
I remember that for some machines, you needed to add a delay before starting conky. 

For example I have some thing like 

> sleep 60 && conky;

I dont remember why this was, but it was said to interefere with the loading (was it Compiz?) It was a long time back, but doesnt hurt in trying this out.

---

### Post by VCoolio on 2009-05-07
Here is a script that checks if conky is running; if yes it kills conky, if no it starts conky after 30 secs. You can refer to it in startup applications or a panel launcher by: sh /path/to/this/script.sh


```
#!/bin/sh
# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else
sleep 30;
conky -c /path/to/config
fi
```

---

### Post by jjrev on 2009-05-07
All, 
Thanks for the quick replies!  It looks like VCoolio's solution is the winner - many thanks! :smile:

---

