---
title: "Conky window  question"
date: 2009-05-30
forum: General Help
---

### Post by ontwowheels on 2009-05-30
Hello,

Quick question, I am very happy with my conky config except for one thing.  As you can see in my screen shot, I get a line or frame around the conky display and I think it has something to do with the conky window.

Any suggestions?  I tried several changes to my conkyrc file but none have helped.

In the screen shot, you can see the frame I am referring to by looking for the mouse pointer.

THANKS

---

### Post by pauna on 2009-05-30
Check your .conkyrc, you should probably have

draw_outline no
draw_borders no
draw_shades no

Do you have these set? If you do, post your .conkyrc and we can debug further.

---

### Post by m_duck on 2009-05-30
It's more likely to be compiz putting a shadow on it I think. You can either stop it happening from the compiz settings manager, though I'm not sure where, or just delay the startup of conky so it loads after compiz.

---

### Post by ontwowheels on 2009-05-30
> **pauna said:**
> Check your .conkyrc, you should probably have

draw_outline no
draw_borders no
draw_shades no

Do you have these set? If you do, post your .conkyrc and we can debug further.

Yes, those are set to no and thanks for responding....

Here is the conkyrc

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
draw_shades no

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
xftfont Terminus:size=9
xftalpha 0.8
#xftfont HandelGotD:size=9
#xftalpha 0.5


TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 ff0000 ff00ff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes
${offset 240}CPU0 ${cpu cpu1}% ${color lightgray}${cpubar cpu1}$color
${offset 240}CPU1 ${cpu cpu2}% ${color lightgray}${cpubar cpu2}$color


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

${offset 240}${color slate grey}NET: 
${offset 240}${color #888888}ip address: ${color #CCCCCC}${addr wlan0}
${offset 240}${color}Up: ${color }${upspeed wlan0} k/s
${offset 240}${upspeedgraph wlan0 20,130 ff0000 0000ff}
${offset 240}${color}Down: ${color }${downspeed wlan0}k/s${color}
${offset 240}${downspeedgraph wlan0 20,130 ff0000 0000ff}

---

### Post by ontwowheels on 2009-05-30
> **m_duck said:**
> It's more likely to be compiz putting a shadow on it I think. You can either stop it happening from the compiz settings manager, though I'm not sure where, or just delay the startup of conky so it loads after compiz.

I have conky start on startup, but if I kill it and start it again it still has that ugly shading around it.

And thanks for the help...

---

### Post by m_duck on 2009-05-31
Someone with the same problem has solved it [thread=624851]here[/thread] from a compiz issue. There are two solutions in the thread.

---

### Post by ontwowheels on 2009-05-31
> **m_duck said:**
> Someone with the same problem has solved it [thread=624851]here[/thread] from a compiz issue. There are two solutions in the thread.


THANKS...I'll check it out.

---

### Post by ontwowheels on 2009-05-31
> **m_duck said:**
> Someone with the same problem has solved it [thread=624851]here[/thread] from a compiz issue. There are two solutions in the thread.

PERFECT.  The last message in the thread fixed me up.  I had searched the forum and came up empty.

Thanks again

---

