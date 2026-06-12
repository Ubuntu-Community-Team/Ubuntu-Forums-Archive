---
title: "Problems with conky scripts"
date: 2010-05-24
forum: Desktop Environments
---

### Post by netbook on 2010-05-24
Hello all. 

I am just trying to get conky configured but after hours of searching I simply cannot get a couple of things to work. I am using someone else's script but I am trying to get it to be transparent as well as hide behind my other windows. Right now it has a black background and stays "on top" no matter what I do. Here is the script I have in my .conkyrc file, any experts want to chime in here?

use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58



TEXT
 ${color 6694B2}${font OpenLogos:size=45} u t
${color BADCDD}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   ${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color F8DF58}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py [email]something[/email] something 3}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}


Thanks, 

Netbook

---

### Post by wojox on 2010-05-24
Try fiddling around with mine:

```

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



```

---

### Post by stinkeye on 2010-05-24
I just ran your .conkyrc config and it is transparent and below other windows.
Are you loading the correct config?

If you enter **conky** in the terminal it will load .conkyrc if it is in your home folder.

If there is no .conkyrc in your home folder it will load the default config at
/etc/conky/conky.conf

To load a specific conky config in terminal use
```
conky -c /path/to/your/config
```

The default conky config at /etc/conky/conky.conf looks like the attached pic, which is probably what you're loading.
I don't know how much you know about conky but you will also need the scripts it is running. eg  conditions.sh and gmail_parser.py
You will also need the extra fonts that it is using. eg OpenLogos, StyleBats

---

### Post by davitodd on 2010-05-27
For the conky type, try to use:

own_window_type normal
background yes

---

