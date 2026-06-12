---
title: "conky horizontal help"
date: 2011-12-30
forum: Desktop Environments
---

### Post by joplass on 2011-12-30
Please I need some help with this conky.  I would like to have it horizontal in the following form:
Time  Kernel   Up
Date  CPU      Down
      RAM      Upload
               Download.  

Here is the script and I have attached a screenshot of that conky current lay out. 
[img]http://666kb.com/i/bzyw2uboftcipov1i.jpg[/img]
[PHP]# border width
border_width 1

# Default colors and also border colors
default_color gray
own_window_colour gray

# Text alignment, other possible values are commented
alignment bottom_left

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 45

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
${alignc 35}${font Cantarell MS:size=26}${time %H:%M}${font}
${alignc}${time %a %d %b %Y}

Kernel:  ${alignr}${kernel}
CPU: ${cpu cpu}% ${alignr}${cpubar 8,60 cpu}
RAM: $memperc% ${alignr}${membar 8,60}

${if_existing /proc/net/route eth0}
Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 789E2D A7CC5C}
Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 789E2D A7CC5C}
Upload: ${alignr}${totalup eth0}
Download: ${alignr}${totaldown eth0}[/PHP]

---

### Post by Frogs Hair on 2011-12-30
This page may help with moving items in the .conkyrc . Make a copy of the .conkrc and rename it before you start experimenting . [http://conky.pitstop.free.fr/wiki/index.php5?title=Goto/offset/voffset_(en](http://conky.pitstop.free.fr/wiki/index.php5?title=Goto/offset/voffset_(en))

See the Conky man pages as well .```
man conky
```

---

### Post by joplass on 2011-12-30
Thanks for your suggestion.  I will look into that.

---

### Post by Sector11 on 2012-01-21
> **Frogs Hair said:**
> This page may help with moving items in the .conkyrc . Make a copy of the .conkrc and rename it before you start experimenting . [http://conky.pitstop.free.fr/wiki/index.php5?title=Goto/offset/voffset_(en](http://conky.pitstop.free.fr/wiki/index.php5?title=Goto/offset/voffset_(en))

See the Conky man pages as well .```
man conky
```

That link broken: try this one: [Goto/offset/voffset]("http://conky.pitstop.free.fr/wiki/index.php5?title=Goto/offset/voffset_%28en%29")

One more thing as you create this new conky use the (\) to break lines in your text editor but will continue as one line in conky:

```
TEXT
Time\
${goto xx}Kernel\
${goto xx}Up\
${goto xx}Date\
${goto xx}CPU\
${goto xx}Down\
${goto xx}RAM\
${goto xx}Upload\
${goto xx}Download
```

Makes finding things a LOT easier, also a mono font will really help!

---

