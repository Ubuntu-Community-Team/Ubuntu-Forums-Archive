---
title: "Trouble with conky..."
date: 2011-02-02
forum: Desktop Environments
---

### Post by dr.pepper23 on 2011-02-02
I've got this conkyrc file I downloaded from some website.

```

# Use Xft?
use_xft yes
xftfont Ubuntu:size=11
xftalpha 0.8

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Draw shades?
draw_shades no

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 500
maximum_width 1000

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
# border_margin 0

# border width
border_width 0

# Default colors and also border colors
default_color white
#default_shade_color black 
#black
#default_outline_color white


# Text alignment, other possible values are commented
#alignment bottom_middle
alignment top_middle

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 0
gap_y 0

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 1

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

# Strictness of if_up. One of: up, link or address. The later ones imply the further ones.
# Defaults to up.
if_up_strictness address

TEXT

${color 39e4ee}${font Distress:size=9}#
# Cell 1,1
 S  $font$color${tab 30,0}${font Base 02:size=9}M${font} ${machine} machine running $sysname#
#
# Cell 1,2
${tab 155,0}${font Base 02:size=9}HDD:${font}${tab 193,0}$color${fs_free /}${color 019db6} free of $color${fs_size /}#
#
# Cell 1,3
${tab 280,0}${font Base 02:size=9}Uptime:${font} $uptime#
#
# Cell 1,4
${tab 405,0}${color 39e4ee}${font Base 02:size=9}5 Processes${font} ${tab 457,0}${color 019db6}CPU% MEM%
${color 39e4ee}${font Distress:size=9}#
#
# Cell 2,1
 Y I $font$color${tab 30,0}     with $kernel KERNEL#
#
# Cell 2,2
${tab 155,0}${color white}${fs_bar 8,220 /}#
#
# Cell 2,3
${tab 280,0}${font Base 02:size=9}Battery:${font} ${battery BAT1} ${battery_time BAT1}#
#
# Cell 2,4
${tab 405,0}${color white}${font Ubuntu:size=8}${top_mem name 1}$font${tab 458,0}${top_mem cpu 1}${top_mem mem 1}
${color 39e4ee}${font Distress:size=9}#
#
# Cell 3,1
 S N $font$color${tab 30,0}${font Base 02:size=9}CPU 1 and 2:${font}${tab 85,0}${cpubar cpu1 8,48} - ${cpubar cpu2 8,49}#
#
# Cell 3,2
${tab 155,0}${color 39e4ee}${font Base 02:size=9}Network${font}${tab 224,0}WiFi${if_up wlan0}${color green}ON$else${color darkred}OFF$endif$color#
#
# Cell 3,3
${tab 280,0}${color 39e4ee}Wired${if_up eth0}${color green}ON$else${color darkred}OFF$endif#
#
# Cell 3,4
${tab 405,0}${color white}${font Ubuntu:size=8}${top_mem name 2}$font${tab 458,0}${top_mem cpu 2}${top_mem mem 2}
${color 39e4ee}${font Distress:size=9}#
#
# Cell 4,1
 T F $font$color${tab 30,0}${font Base 02:size=9}CPU 3 and 4:${font} ${tab 85,0}${cpubar cpu3 8,48} - ${cpubar cpu4 8,49}#
#
# Cell 4,2
${tab 155,0}${if_up wlan0}${color 39e4ee}${font Base 02:size=9}WiFi${font} ${color gray}${font Ubuntu:size=8}${addr wlan0}  $color${pre_exec wget -O - http://ip.tupeux.com | tail}$font$endif#
#
# Cell 4,3
${tab 280,0}${if_up eth0}${color 39e4ee}${font Base 02:size=9}Wired${font} ${color gray}${font Ubuntu:size=8}${addr eth0}  $color${pre_exec wget -O - http://ip.tupeux.com | tail}$font$endif#
#
# Cell 4,4
${tab 405,0}${font Ubuntu:size=8}${color white}${top_mem name 3}$font${tab 458,0}${top_mem cpu 3}${top_mem mem 3}
${color 39e4ee}${font Distress:size=9}#
#
# Cell 5,1
 E O $font$color${tab 30,0}${font Base 02:size=9}RAM:${font} ${tab 44,0}$memperc%${tab 85,0}${membar 8,108}#
#
# Cell 5,2
${tab 155,0}${if_up wlan0}${color green}${font Eyecicles:size=9:bold}a$font$color ${upspeed wlan0}${tab 200,0}${font Base 02:size=9}T: $font${totalup wlan0}${tab 240,0}${upspeedgraph wlan0 10,50}$endif#
#
# Cell 5,3
 ${tab 280,0}${if_up eth0}${color green}${font Eyecicles:size=9:bold}a$font$color ${upspeed eth0}${tab 325,0}${font Base 02:size=9}T: $font${totalup eth0}${tab 365,0}${upspeedgraph eth0 10,50}$endif#
#
# Cell 5,4
${tab 405,0}${color white}${font Ubuntu:size=8}${top_mem name 4}$font${tab 458,0}${top_mem cpu 4}${top_mem mem 4}
${color 39e4ee}${font Distress:size=9}#
#
# Cell 6,1
 M   $font$color${tab 30,0}${font Base 02:size=9}SWAP:${font} ${tab 44,0}$swapperc%${tab 85,0}${swapbar 8,108}#
#
# Cell 6,2
${tab 155,0}${if_up wlan0}${color darkred}${font Eyecicles:size=9:bold}b${font}$color ${downspeed wlan0}${tab 200,0}${font Base 02:size=9}T: $font${totaldown wlan0}${tab 240,0}${downspeedgraph wlan0 10,50}$endif#
#
# Cell 6,3
${tab 280,0}${if_up eth0}${color darkred}${font Eyecicles:size=9:bold}b$font$color ${downspeed eth0}${tab 325,0}${font Base 02:size=9}T: $font${totaldown eth0}${tab 365,0}${downspeedgraph eth0 10,50}$endif#
#
# Cell 6,4
${tab 405,0}${color white}${font Ubuntu:size=8}${top_mem name 5}$font${tab 458,0}${top_mem cpu 5}${top_mem mem 5}
${color 39e4ee}${font Distress:size=9}${hr 1} 
${tab 410,0}${font Distress:size=47}${color 39e4ee}${time %H:%M}${font Distress}:${time %S}$color
${tab 410,0}${voffset -6}${font Base 02:size=18}${time %B}$font${font Ubuntu:size=20:bold}${time %d}$font${font Base 02:size=18}${time %Y}$font
${tab 435,0}${voffset -8}${font Base 02:size=16}${time %A}$font
${color 39e4ee}${font Base 02:size=14:bold}#
${hr 1}



```For some reason nothing shows up. I save this file as .conkyrc in my home folder and run it by typing conky into the terminal. This is output:

```

cody@cody-laptop:~$ conky
--2011-02-02 21:51:14--  http://ip.tupeux.com/
Resolving ip.tupeux.com... 88.191.122.240
Connecting to ip.tupeux.com|88.191.122.240|:80... Alarm clock
cody@cody-laptop:~$ connected.
HTTP request sent, awaiting response... 200 OK
Length: 14 [text/html]
Saving to: `STDOUT'

100%[==================================================================================================================================>] 14          --.-K/s   in 0s      

2011-02-02 21:51:16 (941 KB/s) - written to stdout [14/14]





```Could someone please explain this to me?

---

### Post by dr.pepper23 on 2011-02-02
I changed the draw_shades option to yes and got it show up on the screen. But it still doesn't look quite right. Attached a screen grab.


Actually I can only get this to work if I start conky with a working script then replace the script while it is already running. Don't know why this happens...

Edit: Think i know what it is. Has to do with this line

```

# Cell 4,2
${tab 155,0}${if_up wlan0}${color 39e4ee}${font Base 02:size=9}WiFi${font} ${color gray}${font Ubuntu:size=8}${addr wlan0}  $color${pre_exec wget -O - http://ip.tupeux.com | tail}$font$endif#
#

```

---

