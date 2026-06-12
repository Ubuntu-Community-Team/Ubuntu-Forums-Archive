---
title: "Conky Snapping"
date: 2009-05-07
forum: General Help
---

### Post by reaperfh on 2009-05-07
I have conky set up and it's running pretty smooth!
There is just one thing that bothers me! I have Compiz installed, using Wobbly Windows and if i move a window around the screen the window always gets stuck to conky's border...
like so:
[[IMG]http://img411.imageshack.us/img411/3012/weirdconky.th.png[/IMG]](http://img411.imageshack.us/my.php?image=weirdconky.png)


This is what i've come up with so far:
If i add the rule "!title=^conkywindow$" (i have set conky's title to be exactly that) to the Windows to Decorate in Compiz nothing happens...
If i change the own_window_type to "desktop" in .conkyrc I get exactly what I want, but for some reason everything it displays on the desktop it stays there.
like so:
[[IMG]http://img411.imageshack.us/img411/6108/screenshotnye.th.png[/IMG]](http://img411.imageshack.us/my.php?image=screenshotnye.png)

So is there a way to make Compiz ignore conky? Or any other kind of workaround? I'm not interested in disabling the effect!

anyway here is my .conkyrc:
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
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_title "conkywindow"
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

text_buffer_size 2400
max_user_text 32000
max_specials 1024

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Total number of times for Conky to update before quitting. Zero makes Conky run forever 
total_run_times 0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
#own_window_colour hotpink
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y -100

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
reaper @ $nodename using $sysname $kernel on $machine
Uptime: ${uptime}

${color orange}CPU ${hr 2}$color
Temp: ${acpitemp}  Load: ${loadavg}    ${freq}MHz
${cpubar cpu1}
${cpubar cpu2}
${cpugraph cpu0 000000 ffffff}
CPU                PID     CPU%      MEM%
 ${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
 ${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
 ${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
 ${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
 ${top name 5} ${top pid 5}   ${top cpu 5}    ${top mem 5}

${color orange}MEMORY ${hr 2}$color
RAM:  $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

RAM                PID     CPU%      MEM%
 ${top_mem name 1} ${top_mem pid 1}   ${top_mem cpu 1}    ${top_mem mem 1}
 ${top_mem name 2} ${top_mem pid 2}   ${top_mem cpu 2}    ${top_mem mem 2}
 ${top_mem name 3} ${top_mem pid 3}   ${top_mem cpu 3}    ${top_mem mem 3}
 ${top_mem name 4} ${top_mem pid 4}   ${top_mem cpu 4}    ${top_mem mem 4}
 ${top_mem name 5} ${top_mem pid 5}   ${top_mem cpu 5}    ${top_mem mem 5}

${color orange}DISK ${hr 2}$color
Root:    ${fs_free /}${fs_bar 6 /}$color${if_mounted /media/Ext}
Ext:     ${fs_free /media/Ext}${fs_bar 6 /media/Ext}$color${endif}${if_mounted /media/HORNY}
Horny:   ${fs_free /media/HORNY}${fs_bar 6 /media/HORNY}$color${endif}

Temp: ${hddtemp /dev/sda}
${diskiograph /dev/sda 000000 ffffff}${if_existing /sys/class/net/wlan0/operstate up}

${color orange}WIRELESS NETWORK [wlan0] (${addr wlan0}) ${hr 2}$color
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0 25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
Conections: ${tcp_portmon 1 65535 count}${endif}${if_existing /sys/class/net/eth0/operstate up}

${color orange}WIRED NETWORK [eth0] (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Conections: ${tcp_portmon 1 65535 count}${endif}

${color orange}LOGGING ${hr 2}$color
${execi 3 dmesg | tail -n 5| fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 3600 fortune -s | fold -w50}

```

---

### Post by maheshasolkar on 2009-05-07
Can you try to set own_window_type to 'override' or 'desktop' and see if it works any better?

---

### Post by reaperfh on 2009-05-08
well desktop gives me that weird freeze effect but infact it doesn't have sticky borders...
if I set it to override it doesn't even show up... it gets drawn below my wallpaper. If I change the Window Manager to Metacity, I can see it yet it's shifted up. =/

---

### Post by reaperfh on 2009-05-11
no one?

*bump*

---

### Post by reaperfh on 2009-05-15
bamp...

---

### Post by reaperfh on 2009-05-19
anyone? =/

---

### Post by VCoolio on 2009-05-19
Aren't you talking about the Snapping Windows plugin? In the Behavior tab you can untick the window edges options, so windows only stick to screen edges instead of window borders.

---

### Post by reaperfh on 2009-05-19
I know that! But I just want to disable it for conky in specific! the rest can stay...

---

### Post by whitethorn on 2009-05-19
Do you have conky start after compiz? I don't have that problem at all and my conkyrc is almost the same as yours. Do you have any other rules about conky in Compiz?

---

### Post by reaperfh on 2009-05-20
yeah, conky starts with a 30sec delay so it doesn't get stuck underneath the gnome-panel.
And no I don't have any other rules regarding conky in compiz... =/

---

### Post by whitethorn on 2009-05-20
Hi, 

So I took a closer look at your conkyrc.  I tried it out and I have the same problem as you.  I then changed the following line.

> own_window_type normal

to 

> own_window_type override

I hope this helps fixes it.

Oops just read through the past posts.  Seems override isn't an option.  Wierd it works for me with compiz running.

---

### Post by AwesomeIncarnate on 2009-08-11
> **reaperfh said:**
> 
If i change the own_window_type to "desktop" in .conkyrc I get exactly what I want, but for some reason everything it displays on the desktop it stays there.

Sorry to dig up an old thread, but I had the same problem and thought I'd share my solution.

If you change own_window_type to "dock", conky will not minimize when you show desktop, and not have the moving windows problem.

---

