---
title: "Conky help"
date: 2008-01-16
forum: Desktop Environments
---

### Post by Fraser from Scotland on 2008-01-16
Hey, I just installed conky and I have managed to change a couple of things but I would really like a fan speed teller thing and my network connection in conky. Can someone please tell me how to do this? I am totally knew to it. Here is my .conkyrc    (Sorry i dont know how to do the code box)

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
own_window_hints undecorated,below,skip_taskbar
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

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}

${offset 240}${color slate grey}FILESYSTEM:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}

---

### Post by Fraser from Scotland on 2008-01-16
Im off to bed. bump.

---

### Post by taavikko on 2008-01-17
Might wanna check out this,
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by Fraser from Scotland on 2008-01-17
> **taavikko said:**
> Might wanna check out this,
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

Yeah I've seen that, but I don't know how to implement that information.

---

### Post by Fraser from Scotland on 2008-01-17
Can someone help?

---

### Post by yoyodyne on 2008-01-17
There is a "conky startup examples" thread somewhere...I found it at one time. It had screenshots to go along with the sample .conkyrc files...pretty handy.

You could probably copy and paste from those examples to get a working config.

---

### Post by aonegodman on 2008-01-17
I just figured out how to stop it and get it off my desktop.

In terminal I entered "conky stop" <return>

It stopped, I closed terminal window. Next, I had to mouse over the conky screen on my desktop(created a text box with mouse) to refresh or remove conky off screen.

Hope this helps someone.  :)

---

### Post by WiFi Ed on 2008-01-17
Try this thread for every possible conky variation. There are pics and .conkyrc files in abundance...:)

[http://www.ubuntuforums.org/showthread.php?t=281865]("http://www.ubuntuforums.org/showthread.php?t=281865")

---

