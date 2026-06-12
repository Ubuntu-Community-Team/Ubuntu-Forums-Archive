---
title: "conky.rc error.."
date: 2011-07-22
forum: Desktop Environments
---

### Post by moonsal on 2011-07-22
Hey ya'll.... I'm having the damndest time with conky... No matter which conky.rc I use I ALWAYS get this msg.. I just don't understand it? I've even tried some REALLY simple scripts but to no avail.. Any ideas from the conky gurus.. :P

```
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: forked to background, pid is 1852

moonsal@ubuntu:~$ Conky: desktop window (2000003) is subwindow of root window (63)
Conky: window type - override
Conky: drawing to created window (0x4600001)
Conky: drawing to double buffer
Conky: obj->data.i 2 info.cpu_count 1
Conky: attempting to use more CPUs than you have!

```

---

### Post by Toz on 2011-07-22
> **moonsal said:**
> Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Looks like you have the statement ```
use_spacer yes
``` in the file when it is expecting left, right, or none. So its going to assume you mean right
> Conky: forked to background, pid is 1852
Running in the background...

> Conky: desktop window (2000003) is subwindow of root window (63)
Conky: window type - override
Conky: drawing to created window (0x4600001)
Conky: drawing to double bufferJust regular messages
> Conky: obj->data.i 2 info.cpu_count 1
Conky: attempting to use more CPUs than you have!
Looks like your file makes reference to 2 cpus when you only have 1.

Does conky display on your screen? 
Any chance you could post one of these .conkyrc files that you are trying to use?

---

### Post by moonsal on 2011-07-22
I do hope this is the right place for this post...

Nothing displays at all... And one of the scripts I tried to get to work was the first one posted in the thread "Show us you conky.rc file" It seems no matter which script I use I always end up with the same outcome... I am just about ready (been meaning to anyways) to format my Win7 box and install ubuntu on it... This system is only a 1Ghz PIII w/ 192 MB RAM... My other box is a Celeron 2.53 w/ 1.25gig RAM.. Not much better but a little..
Could the system be the reason?

```

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
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}
```

---

### Post by mips on 2011-07-22
```
use_spacer yes
```

Options for use_spacer = left, right or none. There is no 'yes' option.


Try my config and see if you get any errors,

```

alignment tr
double_buffer yes
gap_x 10
gap_y 40
own_window no
own_window_type desktop
own_window_transparent yes
use_xft yes
font snap


TEXT
${color 666666}
Now Playing $hr
    ${if_running audacious}${exec audtool current-song-tuple-data title} - ${exec audtool current-song-tuple-data artist}
    ${exec audtool --current-song-bitrate-kbps} kbps / ${exec audtool --current-song-length} ${execbar expr 100 \* $(audtool --current-song-output-length-seconds) \/ $(audtool --current-song-length-seconds)}$endif



System $hr
    ${execi 30 hostname}
    Kernel: $alignr$kernel
    Uptime: $alignr$uptime

CPU $hr
    ${freq_g}GHz    ${alignc}${loadavg}    $cpu% ${alignr}${hwmon temp 1}°C
    ${cpugraph 15,0 ffff0C 666666}
    ${top name 1} ${alignr}${top cpu 1}%
    ${top name 2} ${alignr}${top cpu 2}%
    ${top name 3} ${alignr}${top cpu 3}%
    ${top name 4} ${alignr}${top cpu 4}%

Memory $hr
    RAM ${alignr}$mem/$memmax ${membar 6, 75}
    Swap ${alignr}$swap/$swapmax ${swapbar 6, 75}

    ${top_mem name 1}${alignr}${top_mem mem 1}%
    ${top_mem name 2}${alignr}${top_mem mem 2}%
    ${top_mem name 3}${alignr}${top_mem mem 3}%
    ${top_mem name 4}${alignr}${top_mem mem 4}%

Disk $hr
    / ${alignr}${fs_free /} ${fs_free_perc /}% ${fs_bar 6, 75 /}
    /home ${alignr}${fs_free /home} ${fs_free_perc /home}% ${fs_bar 6, 75 /home}
    Temp: ${alignr}${hddtemp /dev/sda}°C

Battery $hr
    Charge ${alignr}${battery_time C174}${battery_percent C174}% ${alignr}${battery_bar 6,100 C174}
    AC-Adapter${alignr}$acpiacadapter

Network $hr
    Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
    ${downspeedgraph eth0 15,100 ffff0C 666666} ${alignr}${upspeedgraph eth0 15,100 ffff0C 666666}
    Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

```

Your computers are fine, don't worry about them. This is a software issue.
What version of Ubuntu & Conky are you running?




.

---

### Post by lisati on 2011-07-22
*Thread moved to **Desktop Environments**.*

---

### Post by moonsal on 2011-07-22
Sorry about the placement of this thread... 

Tried that script and and the same thing...

```
@ubuntu:~$ conky
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: forked to background, pid is 1377
me@ubuntu:~$ 
Conky: desktop window (2000003) is subwindow of root window (63)
Conky: window type - override
Conky: drawing to created window (0x4e00001)
Conky: drawing to double buffer
Conky: obj->data.i 2 info.cpu_count 1
Conky: attempting to use more CPUs than you have!
killall conky
conky: no process found

```

Running Xubuntu 10.04.... Conky 1.8.0

---

### Post by moonsal on 2011-07-22
I'm a dyslexic inbred fool...HAHAHA I had my file named conky.rc not .conkyrc... WOW... 

Do have another problem though, I know it needs some editing on my part but why does my Desktop icons disappear and I have to move my cursor over them to make them appear again (minus txt too)...

---

### Post by mips on 2011-07-22
> **moonsal said:**
> Sorry about the placement of this thread... 

Tried that script and and the same thing...


Are you actually specifying what config file conky should use?

Save the config file in ~/.conky/

Invoke conky with,
```
conky -c ~/.conky/conkyrc
```

I know I'm stating the obvious but you never know.

---

### Post by mips on 2011-07-22
> **moonsal said:**
> I'm a dyslexic inbred fool...HAHAHA I had my file named conky.rc not .conkyrc... WOW... 

Do have another problem though, I know it needs some editing on my part but why does my Desktop icons disappear and I have to move my cursor over them to make them appear again (minus txt too)...

Lol.

Sorry, don't have xfce so no idea.

---

### Post by moonsal on 2011-07-22
No worries... Thanks for the help though...

---

### Post by mips on 2011-07-22
[http://conky.sourceforge.net/faq.html](http://conky.sourceforge.net/faq.html)
> Q: Why does Conky make my icons disappear?

A: Conky is probably fighting with your desktop manager over drawing to the root window. A quick and easy fix (in your conkyrc):

```
own_window yes
own_window_type desktop # Try also 'normal' or 'override'
See also "Conky won't stop flickering"
```

[http://saraithegeek.wordpress.com/2009/04/15/how-to-fix-conky-flickering-borders-and-drop-shadows/](http://saraithegeek.wordpress.com/2009/04/15/how-to-fix-conky-flickering-borders-and-drop-shadows/)
[http://ubuntuforums.org/showthread.php?t=1558054](http://ubuntuforums.org/showthread.php?t=1558054)




.

---

### Post by moonsal on 2011-07-22
mips.... You da 5h|T!!!!!!!!!!11 Fixed it spot on.... I guess I need to learn to broaden my search skills..LOL

Thanks...

---

