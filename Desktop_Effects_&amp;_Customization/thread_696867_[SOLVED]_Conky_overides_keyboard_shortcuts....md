---
title: "[SOLVED] Conky overides keyboard shortcuts..."
date: 2008-02-14
forum: Desktop Effects &amp; Customization
---

### Post by geo909 on 2008-02-14
Hello everybody.
I have conky  in my desktop and
I really love  it, it is extremely useful. Well, the thing is that whenever I close a window, keyboard shortcuts do not work unless I click on the desktop...

 I know that sounds extremely useless to fix, but it is important for me as It's been a while since I used to do things entirely with keyboard (it's soo faster). So it becomes really frustarting.
Could someone please help me with it? I would be grateful...

Is there a way I could make it appear as a screenlet? 

This is the conky configuration file. The red lines seem to be the important ones for my case:

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
# -- Pengo (conky@pengo.us)
#

[COLOR="Red"]# Create own window instead of using desktop (required in nautilus)
own_window yes
#own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager[/COLOR]

background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 50 4

maximum width 10

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 1

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
gap_x 30
gap_y 50

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${color slate grey}${time %a, } ${color }${time %e %B %G}
${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${color slate grey}UpTime: ${color }$uptime
${color slate grey}Kern:${color }$kernel

-----------------------------------------

${color #A1CF31}CPU:${color orange} $cpu% 
${cpugraph 20,130 000000 ffffff}
${color slate grey}Load: ${color }$loadavg
${color slate grey}Processes: ${color }$processes  
${color slate grey}Running:   ${color }$running_processes

${color slate grey}Highest CPU:
${color #ddaa00} ${top name 1}${top_mem cpu 1}
${color lightgrey} ${top name 2}${top cpu 2}
${color lightgrey} ${top name 3}${top cpu 3}
${color lightgrey} ${top name 4}${top cpu 4}

-----------------------------------------

${color red}MEM:  ${color #FF881A} $memperc% $mem/$memmax
${color red}${membar 5,150}

${color black}SWAP: ${color black}$swapperc% $swap/$swapmax
${swapbar 5,150}
${color}

${color slate grey}Highest MEM:
${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${color lightgrey} ${top_mem name 4}${top_mem mem 4}

-----------------------------------------

${color blue}FILESYSTEM (/): 
${color grey}used: ${color orange}${fs_used /} ${color grey}of ${color orange}${fs_size /}
${fs_free /}${color orange} ${color grey}free ${color orange}(${fs_free_perc /}%)
${color blue}${fs_bar 5,150 /}

${color blue}WINDOWS (/media/sda1): 
${color grey}used: ${color orange}${fs_used /media/sda1} ${color grey}of ${color orange}${fs_size /media/sda1}
${fs_free /media/sda1}${color orange} ${color grey}free ${color orange}(${fs_free_perc /media/sda1}%)
${color blue}${fs_bar 5,150 /media/sda1}

${color blue}160GB STORAGE (/media/sdb1): 
${color grey}used: ${color orange}${fs_used /media/sdb1} ${color grey}of ${color orange}${fs_size /media/sdb1}
${fs_free /media/sdb1}${color orange} ${color grey}free ${color orange}(${fs_free_perc /media/sdb1}%)
${color blue}${fs_bar 5,150 /media/sdb1}
${color}
-----------------------------------------

${color black}NET: 

${color grey}Down: ${color orange}${downspeed eth0}k/s${color}
${color #A1CF31}${downspeedgraph eth0 40,140 000000 ffffff}
${color grey}Up: ${color orange}${upspeed eth0} k/s ${color}
${color red}${upspeedgraph eth0 20,140 000000 ffffff}

```

---

### Post by trusatori on 2008-02-17
Same ;[

---

### Post by trusatori on 2008-02-17
On second thought...

After some Googling + experimentation, I came up with the following settings:
```
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

It seems to be working great for me at the moment.  Give it a try and see if it gets it done for you.

One slight drawback to these settings is that Conky now doesn't like to immediately startup with the desktop (by putting it in "Sessions").  It will create an instance but never draw itself on screen.  A quick work-around is to create a terribly simple shell script that reads something like:

```
#!/bin/sh

sleep 3
conky
```

Save that into /usr/bin (named something like "start_conky") and give it a "sudo chmod +x /usr/bin/start_conky" in terminal.  Now, instead of having the command "conky" in Sessions, create an entry to run "start_conky" instead.  You may have to mess around with the amount of "sleep" time depending on your system.

Cheers,
\m/ike

---

### Post by geo909 on 2008-02-17
Wow, I really didn't believe that anyone would take the time to answer this!!
Thank you sooo much!!

Yes, that worked for me, I have conky run on startup plus normal keyboard shortcuts, while my mouse is getting dusted in  its base!

Thanks again!

P.S.Well, I will close this thread but if you have the time, could you please explain me what this "sleep" parameter is? I'm such a noob when it comes to scripts and stuff..

---

### Post by trusatori on 2008-02-17
Glad it worked out for you ;]

All the sleep command does is force the system to stop at that line of the script for the given number of seconds before moving on (to run conky).  In this case, It's just allowing Gnome some time to start and draw the desktop before launching Conky.

---

### Post by geo909 on 2008-02-17
Thanks again!

---

