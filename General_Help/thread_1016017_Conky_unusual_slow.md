---
title: "Conky unusual slow"
date: 2008-12-19
forum: General Help
---

### Post by Masquerade on 2008-12-19
Hey everyone.

My problem is: conky is really really slow. It refreshes about every 5 to 10 seconds although update interval is set to 3 or 1 seconds.
Further, it needs about 10 seconds to start up and to disappear.
This is the terminal output:

```
benjamin@moser-linux:~$ conky
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: can't load font 'arial'
Conky: statfs '/media/hda1': No such file or directory
Conky: desktop window (18000c7) is subwindow of root window (188)
Conky: window type - override
Conky: drawing to created window (0x2400003)
Conky: drawing to double buffer
Conky: statfs '/media/hda1': No such file or directory
(Es konnten nicht alle Prozesse identifiziert werden; Informationen über
nicht-eigene Processe werden nicht angezeigt; Root kann sie anzeigen.)
Conky: statfs '/media/hda1': No such file or directory
(Es konnten nicht alle Prozesse identifiziert werden; Informationen über
nicht-eigene Processe werden nicht angezeigt; Root kann sie anzeigen.)

```
For people who dont understand german^^: Not all processes can be identified; information about not-owned processes wont be shown, root can show them.

This is my .conkyrc
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
# -- Seldon77 (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 1.0

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

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
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

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda1:  ${fs_free_perc /media/hda1}%   ${fs_bar 6 /media/hda1}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
Connections: ${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print "   ",$5,$6,$7,$8,$9,$10}' | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

I am running ubuntu hardy with compiz.

---

### Post by easybake on 2008-12-20
> **Masquerade said:**
> Hey everyone.

My problem is: conky is really really slow. It refreshes about every 5 to 10 seconds although update interval is set to 3 or 1 seconds.
Further, it needs about 10 seconds to start up and to disappear.
This is the terminal output:

```
benjamin@moser-linux:~$ conky
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: can't load font 'arial'
Conky: statfs '/media/hda1': No such file or directory
Conky: desktop window (18000c7) is subwindow of root window (188)
Conky: window type - override
Conky: drawing to created window (0x2400003)
Conky: drawing to double buffer
Conky: statfs '/media/hda1': No such file or directory
(Es konnten nicht alle Prozesse identifiziert werden; Informationen über
nicht-eigene Processe werden nicht angezeigt; Root kann sie anzeigen.)
Conky: statfs '/media/hda1': No such file or directory
(Es konnten nicht alle Prozesse identifiziert werden; Informationen über
nicht-eigene Processe werden nicht angezeigt; Root kann sie anzeigen.)

```
For people who dont understand german^^: Not all processes can be identified; information about not-owned processes wont be shown, root can show them.


Based on my experience, portmon variables can tend to increase update times by alot. You could try to remove them or put them in a separate conky. 

Also you should fix the lines that show up in the error messages:
Remove the font arial line.
Change the user spacer line to true or remove it completely, it is using the default anyway.

You should probably remove the hda1 lines also if they don't work or change them to the proper directory.

---

### Post by Masquerade on 2008-12-20
First, thanks for the answer.
I did what you told me. still the same slow. 

terminal output now looks like the following:
```

conkybenjamin@moser-linux:~$ conky
Conky: desktop window (1a00078) is subwindow of root window (188)
Conky: window type - override
Conky: drawing to created window (0x3400002)
Conky: drawing to double buffer
(Es konnten nicht alle Prozesse identifiziert werden; Informationen über
nicht-eigene Processe werden nicht angezeigt; Root kann sie anzeigen.)
(Es konnten nicht alle Prozesse identifiziert werden; Informationen über
nicht-eigene Processe werden nicht angezeigt; Root kann sie anzeigen.)

```

and .conkyrc:
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
# -- Seldon77 (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_xft no

# Update interval in seconds
update_interval 1.0

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
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
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

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
hda1:  ${fs_free_perc /media/Daten}%   ${fs_bar 6 /media/Daten}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
Connections: ${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | awk '{print "   ",$5,$6,$7,$8,$9,$10}' | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

---

### Post by easybake on 2008-12-20
You could also try to remove the portmon variables. They can really slow down update times. It that doesn't work I really have not idea.

---

### Post by rschauer on 2011-03-28
Wow, this is an ancient thread, but thank you. I was having the same problem with Conky (set to refresh every second, but insisted on refreshing every 6), and removing the portmon lines took care of it. 

Cheers!

---

