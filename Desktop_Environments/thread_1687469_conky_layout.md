---
title: "conky layout"
date: 2011-02-13
forum: Desktop Environments
---

### Post by brivy on 2011-02-13
I'm really stuck with a layout problem in Conky 1.8.1.  If you look at the upper left of the desktop you will see a grey box around time/date window called conky_time.  The lower left window is called conky_network, and of course, the window on the right is .conkyrc.  The whole mess is called up by a script at start time. I changed the "draw_borders" argument to yes in order to show the box and the problem.  How do I shrink the box so that it is just around the date and time?  And once properly shrunk, how do I get it to expand to cover a possible weather addition to go under the date and time?  Thank you in advance.

```
# .conkyrc
# 
# 02_12_2011
#
# 
# 
# 
#


# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

double_buffer yes

use_spacer no
use_xft yes
xftfont Verdana:size=10

update_interval 3.0

minimum_size 250 5
maximum_width 400

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#font verdana
uppercase no # set to yes if you want all text to be in uppercase

stippled_borders 0

border_margin 0

border_width 0

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
alignment middle_right

# Gap between borders of screen and text
gap_x 30
gap_y 0

#just saving it
#${font Verdana:style=Bold:size=9}${color1}Gmail: ${font Verdana:size=8}
#${execi 600 conkyEmail --servertype=IMAP --servername=imap.googlemail.com --#username=brivy2005@gmail.com --password=cobalt55 --ssl} new emails
#$stippled_hr

#${execi 3600 conkyForecast --location=USLA0072 --datatype=LT} / ${execi 3600 conkyForecast --location=USLA0072 --datatype=HT}


# stuff after ‘TEXT’ will be formatted on screen

TEXT
$color 

${color #8BB381}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color #8BB381}CPU ${hr 2}$color
${freq}MHz Load: ${loadavg} Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME PID CPU% MEM%
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

${color #8BB381}MEMORY / DISK ${hr 2}$color
RAM: $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

Root: ${fs_free_perc /}% ${fs_bar 6 /}$color
hda1: ${fs_free_perc /media/hda1}% ${fs_bar 6 /media/hda1}$color
hdb3: ${fs_free_perc /media/hdb3}% ${fs_bar 6 /media/hdb3}

${color #8BB381}BAD PROG ${hr 2}$color
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}


${color #8BB381}OUT CONNECT ${hr 2}$color
${execi 30 netstat -ept | grep ESTAB | awk '{print $9}' | cut -d: -f1 | sort | uniq -c | sort -nr}

${color #8BB381}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

```

```
#conky_time

double_buffer yes
update_interval 1
background yes

own_window yes
own_window_transparent yes
#own_window_type normal
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment middle_right


# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#font verdana
uppercase no # set to yes if you want all text to be in uppercase

use_xft yes
override_utf8_locale no
xftfont Steve:size=30
#xftalpha 0.8
draw_shades no
draw_outline no
draw_borders yes
uppercase no
use_spacer no

```

```
#conky_network
# 
# 02_12_2011
#
# 
# 
# 
#


# Create own window instead of using desktop (required in nautilus)
own_window no
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

double_buffer yes

use_spacer no
use_xft yes
xftfont Verdana:size=10

update_interval 1.0

minimum_size 250 5
maximum_width 400

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#font verdana
uppercase no # set to yes if you want all text to be in uppercase

stippled_borders 0

border_margin 0

```> [QUOTE][/QUOTE]

---

