---
title: "Conky not reading memory usage right"
date: 2009-02-11
forum: General Help
---

### Post by medeshago on 2009-02-11
Conky doesn't output correctly the amount of memory of usage, here's a screenshot of what I'm talking about:

[IMG]http://img26.imageshack.us/img26/5677/screenshot2au3.png[/IMG]

And my conkyrc:

```
own_window yes
own_window_hints undecorated,below,sticky,skip_pager,skip_taskbar
own_window_type override
own_window_transparent yes


background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 300 8
maximum_width 1440

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

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment middle_right
#alignment bottom_left
#alignment bottom_right

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale yes
xftfont Liberation Sans:size=8
xftalpha 0.8

double_buffer yes
alignment top_left
gap_x 5
gap_y 32
#no_buffers yes
use_spacer yes

TEXT
${color forest green}up: ${color chartreuse1}$uptime        ${color forest green}mem ${color chartreuse1}$memperc% ${membar 6,40}        ${color chartreuse1}uso mem ${color forest green} ${top_mem name 1}:${color chartreuse1}${top_mem mem 1} ${color forest green} ${top_mem name 2}:${color chartreuse1}${top_mem mem 2} ${color forest green} ${top_mem name 3}:${color chartreuse1}${top_mem mem 3} ${color forest green} ${top_mem name 4}:${color chartreuse1}${top_mem mem 4} ${color forest green}        ip ${color chartreuse1}${addr eth0}
```

---

### Post by squaregoldfish on 2009-02-12
The top_mem variable lists the percentage of your memory that the process is using, not the real amount in Mb.

I'm not sure if it's possible to have conky display the Mb amount off the top of my head - have a read through the page below to see what's available:

[http://conky.sourceforge.net/variables.html]("http://conky.sourceforge.net/variables.html")

Steve.

---

