---
title: "Conky"
date: 2008-01-14
forum: Desktop Effects &amp; Customization
---

### Post by simwiz on 2008-01-14
Hi, Im a n00b so be patient :P 

ive installed conky and changed the .conkyrc file in my /home/username/ directory. The problem is the window will not be set as the background, its always forced to the front. see image!

ive set background to yes and no i have also tried on_bottom no and yes 

still the window is set to the front....

Any ideas? thanks

config file below

# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check [http://conky.sf.net](http://conky.sf.net) for an up-to-date-list.
# set to yes if you want Conky to be forked in the background
background yes
# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
font arial
# Use Xft?
use_xft no
# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8
# Text alpha when using Xft
xftalpha 0.8
# Print everything to stdout?
# out_to_console no
# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell
# Print everything to console?
# out_to_console no
# mail spool
mail_spool $MAIL
# Update interval in seconds
update_interval 5.0
# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0
# Create own window instead of using desktop (required in nautilus)
own_window yes
# If own_window is yes, you may use type normal, desktop or override
own_window_type override
# Use pseudo transparency with own_window?
own_window_transparent yes
# If own_window_transparent is set to no, you can set the background colour    here
own_window_colour hotpink
# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_hints undecorated,below,sticky
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
# Minimum size of text area
minimum_size 280 5
# Draw shades?
draw_shades no
# Draw outlines?
draw_outline no
# Draw borders around text
draw_borders no
# Draw borders around graphs
draw_graph_borders yes
# Stippled borders?
stippled_borders 8
# border margins
border_margin 4
# border width
border_width 1
# Default colors and also border colors
default_color black
default_shade_color black
default_outline_color black
# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none
# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 35
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
override_utf8_locale no
# Add spaces to keep things from moving about? This only affects certain objects.
use_spacer no
# Allow each port monitor to track at most this many connections (if 0 or not    set, default is 256)
#max_port_monitor_connections 256
# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512
# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384
# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
# stuff after 'TEXT' will be formatted on screen
TEXT
$color $nodename - $sysname $kernel on $machine
$hr

 Uptime:${color #606060} $uptime $color - Load:${color #606060} $loadavg
$color CPU Usage:${color #606060} $cpu% ${cpubar}
${color #606060} ${cpugraph 0000ff 00ec00}
$color RAM Usage:${color #606060} $mem/$memmax - $memperc% ${membar}
$color Swap Usage:${color #606060} $swap/$swapmax - $swapperc% ${swapbar}
$color Processes:${color #606060} $processes $color Running:${color #606060}    $running_processes

$color$hr

$color Name PID CPU% MEM%
${color #ec0000} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #606060} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
 ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
 ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

$color Mem usage
${color #ec0000} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem    mem 1}
${color #606060} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem    mem 2}
 ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

$color$hr

---

### Post by b0rka7a on 2008-01-14
Maybe compiz starts after conky :) Here's a script that will make conky start 30 seconds after your Ubuntu starts (and after compiz too). Just create a new file with the following lines in it:
```
#!/bin/bash
sleep 30 && conky
```
Save it in your home dir (~/ or /home/<username>) as ".conky-start". Go to the terminal and type:
```
chmod +x ~/.conky-start
```
Go to System > Preferences > Sessions > Add:
```
name -- conky
command -- sh ~/.conky-start
```
Next time you start your Ubuntu everything should be okay. :)

---

### Post by Chipter on 2008-01-14
couldn't you just put the code **sleep 30 && conky** in the startup session commands?
why do you have to put it in a shell script?

---

### Post by b0rka7a on 2008-01-14
I dunno :D I didn't thought of it :lolflag:

---

### Post by lvleph on 2008-01-14
> **Chipter said:**
> couldn't you just put the code **sleep 30 && conky** in the startup session commands?
why do you have to put it in a shell script?

I think the main reason why someone might make the script is to have a central file that runs more than one conky. It was something someone used as an example for multiple conkys and people kept with it. That is just my theory, anyway.

---

### Post by amadeus266 on 2008-01-14
You may find this useful as well.. [http://ubuntuforums.org/showthread.php?t=599061&page=2](http://ubuntuforums.org/showthread.php?t=599061&page=2) :guitar:

---

### Post by cammin on 2008-01-15
own_window_type override
it's forcing it to the top
change it to normal or desktop

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)
They have a rundown of all the options they use.

---

### Post by FuturePilot on 2008-01-15
> **Chipter said:**
> couldn't you just put the code **sleep 30 && conky** in the startup session commands?
why do you have to put it in a shell script?

It won't work that way, I've tried it :p

---

### Post by b0rka7a on 2008-01-15
> **cammin said:**
> own_window_type override
it's forcing it to the top
change it to normal or desktop

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)
They have a rundown of all the options they use.

Mine's set to override too:
```
...
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
...
```
:)

---

### Post by simwiz on 2008-01-15
Wow thanks for the replies guys! Brilliant support! 

So my update, i tried own_window_type normal and desktop which didnt display my conky window what so ever which was weird. 

I also tried the shell script which didnt work i also tried 'sleep 30 && conky' straight into the session command but no luck.

any ideas? 

thanks again

---

### Post by simwiz on 2008-01-15
> **cammin said:**
> own_window_type override
it's forcing it to the top
change it to normal or desktop

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)
They have a rundown of all the options they use.

Sorry cammin! you was totally correct. For some reason i had to restart my system twice and BINGO it worked!

EDIT: now its gone again :S since my last restart? 

whats going on !!!!

---

