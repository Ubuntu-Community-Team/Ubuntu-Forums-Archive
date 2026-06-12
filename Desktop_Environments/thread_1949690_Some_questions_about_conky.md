---
title: "Some questions about conky"
date: 2012-03-30
forum: Desktop Environments
---

### Post by L R C on 2012-03-30
I downloaded Conky system monitor today, and I really like it, but I've had some trouble aligning certain things.

I'm using a Gmail script I found [here]("http://ubuntuforums.org/showthread.php?t=680265"), as well as a BBC News RSS feed. I want to have the contents of both aligned to the right, but unfortunately if I put " ${alignr} " at the beginning of a line, only the first news item will be aligned to the right, and the rest to the left - if I do this with the email line, only the line telling me how many emails I have is aligned. Is there any way to fix this?

I also want to know if it's possible to integrate URLs into Conky so that I could be able to go to the news website when I've read the RSS feed.

This is my Conky script, which I based on something I found online (I've left out the " ${alignr} " instructions for the RSS feed and email script):
```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 100

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 0

# border width
border_width 0

# Default colors and also border colors
default_color grey
#default_shade_color black
#default_outline_color grey
own_window_colour grey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 35

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 10

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none


TEXT

${voffset -42}${font OpenLogos:size=150}v
${voffset -275}${font DejaVu Sans:size=8}SYSTEM ${hr 2}          
${voffset 2}${font StyleBats:size=16}${font}   Kernel:  ${alignr -2}${kernel}
${font StyleBats:size=16}${font}   CPU 0: ${cpu cpu0}% ${alignr}${cpubar cpu0 8,60}
${font StyleBats:size=16}${font}   CPU 1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}${font}   HD: ${fs_used /} ${alignr}${fs_bar 8,60 /}
${font StyleBats:size=16}${font}   Uptime: ${alignr}${uptime}

TIME ${hr 2}
${alignr 48}${font Arial Black:size=16}${time %H:%M:%S}${font}
${alignr}${time %A %d %B %Y}

PROCESSES ${hr 2}

NAME $alignr     CPU      RAM
${top name 1} $alignr ${top cpu 1}% ${top mem 1}%
${top name 2} $alignr ${top cpu 2}% ${top mem 2}%
${top name 3} $alignr ${top cpu 3}% ${top mem 3}%
${top name 4} $alignr ${top cpu 4}% ${top mem 4}%
${top name 5} $alignr ${top cpu 5}% ${top mem 5}%

EMAILS ${hr 2} ${alignr}
${execi 60 perl ${alignr} ~/scripts/gmail.pl e}

BBC NEWS ${hr 2} ${alignr}
${rss feeds.bbci.co.uk/news/rss.xml 1 item_titles 3 }
```Thanks in advance for any help. I'd be happy to provide screenshots if necessary.

---

### Post by Frogs Hair on 2012-03-30
Disregard ,   My error .

---

### Post by mrpeachy on 2012-03-31
seek out the main conky config/screenshot thread [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)
more likely to get an answer there

it is possible to do what you want, it just isnt easy and requires lua scripts, you cant do it with regular conky

---

