---
title: "conky question"
date: 2009-06-04
forum: General Help
---

### Post by groovomata on 2009-06-04
Hello All, I have a conky question. In my display I have, under my 'Network' section, wireless and ethernet ip addresses and up and down kb/s. Please refer to my screenshot.
I would like the part of my display that shows the upspeed and downspeed of my internet connection to show the up and downspeed of whichever adapter is connected. Currently, it only shows the output from wlan0.
Does anyone know how I would do that?
Thank you, 
Erik.
Here is my .conkyrc file:
```
# set to yes if you want Conky to be forked in the background
background yes

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Trebuchet MS:size=10

# Text alpha when using Xft
xftalpha 0.9

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 160 5

# Maximum width
maximum_width 160

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders no

# Stippled borders?
# stippled_borders 8

# border margins
# border_margin 2

# border width
# border_width 1

# Default colors and also border colors
default_color white
default_shade_color red
default_outline_color green

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# variable is given either in format $variable or in ${variable}

# stuff after 'TEXT' will be formatted on screen

#  unused text
#  Current:${alignr}${execi 20 /home/tonyt/scripts/.conky_eth2} Mbits/sec
#  hda Temp:${alignr}${execi 1800 /home/tonyt/scripts/.hdtemp}

TEXT
hostname:$alignr$nodename
uptime:$alignr$uptime
$sysname $kernel

Network
wlan0:$alignr${addr wlan0}
eth0:$alignr${addr eth0}
up:$alignr${downspeed wlan0} kb/s
down:$alignr${upspeed wlan0} kb/s

System
cpu0 ${cpu cpu1}% ${color white}${cpubar cpu1}$color
cpu1 ${cpu cpu2}% ${color white}${cpubar cpu2}$color
ram: $memperc% ${color white}$membar$color
swap: $swapperc% ${color white}$swapbar$color
hda1: ${fs_used_perc /}% ${color white}${fs_bar /}$color
hda5: ${fs_used_perc /home}% ${color white}${fs_bar /home/}$color
processes: $processes ${alignr}running: $running_processes
```

---

### Post by Celauran on 2009-06-04
```

Network
${if_up wlan0}
wlan0:$alignr${addr wlan0}
up:$alignr${downspeed wlan0} kb/s
down:$alignr${upspeed wlan0} kb/s
${endif}
${if_up eth0}
eth0:$alignr${addr eth0}
up:$alignr${downspeed eth0} kb/s
down:$alignr${upspeed eth0} kb/s
${endif}

```

---

### Post by gamblor01 on 2009-06-04
Just for a little further explanation (I agree that the above should work -- with one slight tweak):

Your problem is that your .conkyrc is specifically configured to show the speed only for wlan0:

```

Network
wlan0:$alignr${addr wlan0}
eth0:$alignr${addr eth0}
up:$alignr${**downspeed [COLOR=Red]wlan0[/COLOR]**} kb/s
down:$alignr${**upspeed [COLOR=Red]wlan0[/COLOR]**} kb/s

```You could replace the wlan0 values above with eth0 and that would make it show the information for eth0.  The solution given by Celauran does one better than that.  It says if the wlan0 device is configured, then show the info for it.  If eth0 is configured, show the info for it as well.

Also, it appears that you have your up and down speeds backwards (see the black, bold text above -- you have downspeed showing after the "up:" label).  I think you actually want to do this:

```

Network
${if_up wlan0}
wlan0:$alignr${addr wlan0}
up:$alignr${upspeed wlan0} kb/s
down:$alignr${downspeed wlan0} kb/s
${endif}
${if_up eth0}
eth0:$alignr${addr eth0}
up:$alignr${upspeed eth0} kb/s
down:$alignr${downspeed eth0} kb/s
${endif}

```

---

### Post by Celauran on 2009-06-04
> **gamblor01 said:**
> 
Also, it appears that you have your up and down speeds backwards (see the black, bold text above -- you have downspeed showing after the "up:" label).

Oh, good catch. I had completely missed that.

---

### Post by gamblor01 on 2009-06-04
> **Celauran said:**
> Oh, good catch. I had completely missed that.
No problem.  ;)

---

### Post by groovomata on 2009-06-07
Hey Celauran and gamblor01, thanks so much for the help! I greatly appreciate it!
All the best,
Erik.

---

