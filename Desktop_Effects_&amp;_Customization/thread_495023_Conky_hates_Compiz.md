---
title: "Conky hates Compiz"
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by Bofur on 2007-07-07
When I try running conky while Compiz is active, the system information text bleeds into other text, I also get a big black box around it. Heres my conkyrc and any help would be appreciated!
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour brown
own_window_transparent yes

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
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}s
```

---

### Post by Waappu on 2007-07-07
Hi

Type in terminal

```
gksu gedit /etc/X11/xorg.conf
```
and add this line under section "Modules"
```
Load "dbe"
```

---

### Post by Waappu on 2007-07-07
Hi

This post might help
[http://ubuntuforums.org/showthread.php?t=492762&highlight=conky+beryl](http://ubuntuforums.org/showthread.php?t=492762&highlight=conky+beryl)

---

### Post by Bofur on 2007-07-07
It worked, but when I restart, theres a big clear box around it. I've done a killall conky && conky and then restarted it and it's fine again. It happens to only do it on startup. Any ideas? Thanks!

---

### Post by walkerk on 2007-07-07
> **Bofur said:**
> It worked, but when I restart, theres a big clear box around it. I've done a killall conky && conky and then restarted it and it's fine again. It happens to only do it on startup. Any ideas? Thanks!

maybe when you load compiz do it like this
```
sleep 10 && compiz --replace && sleep 30 && conky
```

or w/ emerald

```
sleep 10 && compiz --replace -c emerald && sleep 30 && conky
```

---

### Post by Bofur on 2007-07-07
When I do that compiz doesn't even start =/

---

### Post by ChadMC on 2007-07-07
I start compiz from the session startup as normal with...

**compiz --replace -c emerald**

and also in my session startup, I have

**sh /home/<user_name>/.conky_start.sh**

the **.conky_start.sh** file looks like..

```
#!/bin/bash
sleep 12 && conky;
```

It basically does the same as what walkerk said, but in shorter time.

---

### Post by Bofur on 2007-07-08
Hmm well I tried it and I'm still getting a big box around it. Also, it's on top of all my other windows, I have to kill conky just to make it go away.

---

### Post by Bofur on 2007-07-08
Nevermind, I got it to work.. My problem was that I was trying to run two instances of Conky at startup. Thanks

---

