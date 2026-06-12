---
title: "Applet for downlink/uplink data"
date: 2012-01-11
forum: Desktop Environments
---

### Post by shashanksingh on 2012-01-11
Hi..

Im using 11.10 unity interface.

I wanted to add an applet on my top-panel which would show me the current uplink and downlink data rates.

---

### Post by shashanksingh on 2012-01-15
I tried the system-monitor-load indicator applet.  But it shows me graphs. I would want simple current download and upload numericals...

Ive seen it somewhere but maybe Im not searching correctly

---

### Post by Krytarik on 2012-01-15
> **shashanksingh said:**
> Ive seen it somewhere but maybe Im not searching correctly
Instigated by this, I just searched Google for "indicator unity network", and this is what came up first ;-) , looks promising:

[http://www.webupd8.org/2011/05/how-to-display-network-upload-download.html](http://www.webupd8.org/2011/05/how-to-display-network-upload-download.html)

Regards.

---

### Post by stinkeye on 2012-01-15
Another way is to use conky.
```
sudo apt-get install conky-all
```

Save this as **.conkyrc** in your home folder.
```

####
## Use XFT? Required to Force UTF8 (see below).
#
use_xft yes
xftfont Ubuntu:size=10
xftalpha 0.8
text_buffer_size 512

####
## Force UTF8? Requires XFT (see above).
## Displays degree symbol, instead of Â°, etc.
#
override_utf8_locale yes

####
## Daemonize Conky, aka 'fork to background'.
#
background no

####
## Update interval in seconds.
#
update_interval 1.0

####
## This is the number of times Conky will update before quitting.
## Set to zero to run forever.
#
total_run_times 0

####
## Create own window instead of using desktop (required in nautilus)?
#
own_window yes
own_window_colour 000000
own_window_title conkynet
own_window_type override
own_window_transparent yes
#own_window_hints undecorated,above,sticky,skip_taskbar,skip_pager
default_color ffffff
#own_window_argb_visual yes
#own_window_argb_value 180

####
## Use double buffering? Reduces flicker.
#
double_buffer yes

####
## Draw shades?
#
draw_shades no

####
## Draw outlines?
#
draw_outline no

####
## Draw borders around text?
#
draw_borders no
default_outline_color 7E88C4
####
## Draw borders around graphs?
#
draw_graph_borders no

####
## Print text to stdout?
## Print text in console?
#
out_to_ncurses no
out_to_console no

####
## Text alignment.
#
alignment tl

####
## Minimum size of text area.
#
minimum_size 150
maximum_width 150

####
## Gap between text and screen borders.
#
gap_x 1100
gap_y 2

####
## Shorten MiB/GiB to M/G in stats.
#
short_units yes

####
## Pad % symbol spacing after numbers.
#
pad_percents 0

####
## Pad spacing between text and borders.
#
border_inner_margin 2

####
## Limit the length of names in "Top Processes".
#
top_name_width 10

####
## Subtract file system -/+buffers/cache from used memory?
## Set to yes, to produce meaningful physical memory stats.
#
no_buffers yes

####
## Set to yes, if you want all text to be in UPPERCASE.
#
uppercase no

####
## Number of cpu samples to average.
## Set to 1 to disable averaging.
#
cpu_avg_samples 2

####
## Number of net samples to average.
## Set to 1 to disable averaging.
#
net_avg_samples 2

####
## Add spaces to keep things from moving around?
## Only affects certain objects.
#
use_spacer right

####
## My colors (suit yourself).
#
color0 White
color1 Ivory
color2 Ivory2
color3 Ivory3
color4 FF4040
color5 Tan2
color6 Gray
color7 AntiqueWhite4
color8 orange
#color9 red
color9 6A90EF #icon




TEXT
${color green}${font PizzaDudeBullets:size=12}T${font}${offset 1}${downspeed eth0}${goto 70}${color yellow}${font PizzaDudeBullets:size=12}N${font}${offset 1}${upspeed eth0}
```

Uncompress the attached archive and place the **pizzadude_bullets** folder
into **~/.fonts**.
Create the ~/.fonts folder in your home directory if needed.

The conky window is positioned at the top left with a horizontal offset of 1100.
You may need to change this setting in the **.conkyrc** to suit your resolution.
```
gap_x 1100
```

Click on the network icon in the panel and then **Connection Information**
to check what interface your using.
If it's not **eth0**, change the 2 instances of **eth0** in the last line of the **.conkyrc** to whatever interface your using.

[COLOR="Red"]The unity panel has to be fully transparent to show the conky window[/COLOR].
ccsm > unity > experimental > panel opacity

To run conky, open a terminal and enter **conky**
To run at startup enter this as the command in startup applications.
The **-p 10** will delay the startup for 10 seconds to allow the desktop to finish loading
```
conky -p 10
```


I use conky to show CPU, HDD and GPU temps as well as memory, network and  desk number as shown in the second pic.

---

### Post by shashanksingh on 2012-01-16
> **Krytarik said:**
> Instigated by this, I just searched Google for "indicator unity network", and this is what came up first ;-) , looks promising:

[http://www.webupd8.org/2011/05/how-to-display-network-upload-download.html](http://www.webupd8.org/2011/05/how-to-display-network-upload-download.html)

Regards.

Ah thanks a lot. Just what I needed. :) Experience shows in googling as well.. :P

> **stinkeye said:**
> Another way is to use conky.
```
sudo apt-get install conky-all
```


I use conky to show CPU, HDD and GPU temps as well as memory, network and  desk number as shown in the second pic.

Havn't tried this now, the first solution seems perfect for now. But it seems a nice option too... thanks for elaborating :) I was loosing hope on this.
Will try sometime

---

