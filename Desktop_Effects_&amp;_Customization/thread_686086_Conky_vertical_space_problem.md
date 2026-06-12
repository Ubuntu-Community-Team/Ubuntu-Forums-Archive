---
title: "Conky vertical space problem"
date: 2008-02-02
forum: Desktop Effects &amp; Customization
---

### Post by NovaAesa on 2008-02-02
I installed Conky yesterday and have been busy making my own custom .conkyrc file. I've run into a few problems though. The one that is bothering me the most at the moment is the fact that I can't seem to be able to use all of the vertical space on the screen. It gets down to about 3/4 of the way down and then Conky just stops, leaving some of the text I have specified in .conkyrc cut off. A screenshot is attached to show what is happening (I am highlighting the desktop to show where the cutoff is).

Thanks in advance to anyone who knows how to fix this.

EDIT: Woops forgot to put my .conkyrc in:
```
#
# Peter Stace's Conky Configuration
#
# Last edited 01/02/08
#

# set to yes if you want Conky to be forked in the background
background no

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering to reduce flicker
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Text alignment
alignment top_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 40

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
#uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no

# Sets up the colours
default_color BBBBBB
default_shade_color 000000
default_outline_color 000000
color1 FF8800 #headings
color2 FFFFFF #data
color3 DD6600 #minor headings

TEXT

${color1}SYSTEM ${hr 2}$color
  ${time %A}$alignr${time %F}
  $color2$sysname $kernel$color on $color2$nodename $machine$color
  Uptime: $color2$uptime$color
  Load: $color2$loadavg$color
  Processes: $color2$running_processes$color of $color2$processes$color running
${color1}BATTERY ${hr 2}$color
  Status: $color2$battery $battery_time
${color1}CPU ${hr 2}$color
  Temperature: $color2${acpitemp}°C$color
  ${color3}Core 1$color
   ${color2}Usage: ${cpu cpu1}% $alignr${cpubar cpu1 6,215}$color
   ${color2}${cpugraph cpu1}$color
  ${color3}Core 2$color
   ${color2}Usage: ${cpu cpu2}% $alignr${cpubar cpu2 6,215}$color
   ${color2}${cpugraph cpu2}$color
${color1}MEMORY ${hr 2}$color
  RAM Usage: $color2$mem$color - $color2$memperc% ${membar}$color
  Swap Usage: $color2$swap$color - $color2$swapperc% ${swapbar}$color
${color1}NETWORKING ${hr 2}$color
  ${color3}eth0 - ${addr eth0}$color
   Down: $color2${downspeed eth0} kiB/s$color${alignr}Up: $color2${upspeed eth0} kiB/s$color
   Total: $color2${totaldown eth0}$color${alignr}Total: $color2${totalup eth0}$color
   $color2${downspeedgraph eth0 32,140 default_color default_color}$alignr${upspeedgraph eth0 32,140 default_color default_color}$color
  ${color3}eth1 - ${addr eth1}$color
   Down: $color2${downspeed eth1} kiB/s$color${alignr}Up: $color2${upspeed eth1} kiB/s$color
   Total: $color2${totaldown eth1}$color${alignr}Total: $color2${totalup eth1}$color
   $color2${downspeedgraph eth1 32,140 default_color default_color}$alignr${upspeedgraph eth1 32,140 default_color default_color}$color
${color1}FILE SYSTEMS ${hr 2}$color
  Read: $color2$diskio_read${tab 55}${color}Write: $color2$diskio_write$color
  /       $color2${fs_used /} / ${fs_size /}
  ${fs_bar /}$color
  /home   $color2${fs_used /home} / ${fs_size /home}
  ${fs_bar /home}$color
${color1}PROCESSES ${hr 2}$color
  ${color3}Top CPU$color
    ${top name 1} ${top cpu 1}%
    ${top name 2} ${top cpu 2}%
    ${top name 3} ${top cpu 3}%
  ${color3}Top MEM$color
    ${top_mem name 1} ${top_mem mem 1} MiB
    ${top_mem name 2} ${top_mem mem 2} MiB
    ${top_mem name 3} ${top_mem mem 3} MiB
```

---

### Post by NovaAesa on 2008-02-07
bump

---

### Post by notwen on 2008-02-07
You may want to try tinkering w/ the following code in your conkyrc:

```

# Minimum size of text area
minimum_size 280 5

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 40

```

Not positive, but is the portion being cut off close to the bottom of your screen or is there plenty of room to spare?

---

### Post by NovaAesa on 2008-02-07
Adjusting minimum_size didn't have any effect whatsoever. Changing gap_x and gap_y just adjusted how far the text was from the upper right hand corner. It makes sense that it should be the second number in 'minimum_size' but I guess not (from [http://conky.sourceforge.net/docs.html):](http://conky.sourceforge.net/docs.html):)
```
**minimum_size**  width (height)
    Minimum size of window
```
There is plenty of room to spare at the bottom. I have another 150 pixels or so of horizontal space that I want to utilise.

---

### Post by cammin on 2008-02-08
Try adding

max_user_text = 32000
max_specials = 1024
text_buffer_size = 2400

Those values are roughly double the default values.
I don't think you've exceeded any of them, but you never know.

---

### Post by moljac024 on 2008-02-12
I don't know if you figured it out already but take another look at the config file.

Look for gap x and gap y and see what they read ::)

---

### Post by wladyx on 2008-05-21
Having the same issue, did you find any solutions?
Thanks.

---

### Post by NovaAesa on 2008-05-22
I'm yet to find any solutions. Although, I haven't really been looking lately. I haven't been using Conky anymore after the Hardy upgrade.

---

### Post by kaivalagi on 2008-05-22
Have you tried asking on the #conky irc channel on irc.freenode.net?

The developers are normally available there and can most likely steer you in the right direction...

I have been using conky for quite some time and have never seen this problem, if I had this issue I would head over to #conky.

Hope that helps

---

### Post by Pauln1969 on 2008-06-05
I have just fixed this on mine

text_buffer_size 192

this needs to be added, the default is 128.

---

