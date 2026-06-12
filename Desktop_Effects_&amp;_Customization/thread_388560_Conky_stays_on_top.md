---
title: "Conky stays on top"
date: 2007-03-19
forum: Desktop Effects &amp; Customization
---

### Post by gosh on 2007-03-19
Hi I'm running conky on feisty.
It starts up ok, but then the conky window stays on top of all other windows.
How can I make it to show up only on the desktop?

btw, if I killall conky and then F2->conky, it works ok

---

### Post by kerry_s on 2007-03-19
Post your .conkyrc so we can check your settings. You can try starting conky last, change your startup to> sleep 5; exec conky

---

### Post by gosh on 2007-03-20
This is my .conkyrc:

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

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 200 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
# font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, white90 == #e5e5e5
default_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen
#2Gb $alignc ${fs_used /media/2GB} / ${fs_size /media/2GB} $alignr ${fs_free_perc /media/2GB}%
#${fs_bar /media/2GB}

TEXT
$color
${color brown}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color brown}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}  
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}

${color brown}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}
XP $alignc ${fs_used /media/XP} / ${fs_size /media/XP} $alignr ${fs_free_perc /media/XP}%
${fs_bar /media/XP}
Music $alignc ${fs_used /media/Music} / ${fs_size /media/Music} $alignr ${fs_free_perc /media/Music}%
${fs_bar /media/Music}
Movies $alignc ${fs_used /media/Movies} / ${fs_size /media/Movies} $alignr ${fs_free_perc /media/Movies}%
${fs_bar /media/Movies}
iPod $alignc ${fs_used /media/ipod} / ${fs_size /media/ipod} $alignr ${fs_free_perc /media/ipod}%
${fs_bar /media/ipod}


${color brown}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignc}Status: ${linkstatus eth0} ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color brown}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}

```

---

### Post by kerry_s on 2007-03-20
Did you try using the command i posted? ( sleep 5; exec conky )

If the that command doesn't help, try changing

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

To

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type desktop
own_window_hints below

```


The rest looks okay, did you make sure to turn on double buffer in xorg.conf? ( Load "dbe" )

---

### Post by gosh on 2007-03-21
> **kerry_s said:**
> Did you try using the command i posted? ( sleep 5; exec conky )

If the that command doesn't help, try changing

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```To

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type desktop
own_window_hints below

```
The rest looks okay, did you make sure to turn on double buffer in xorg.conf? ( Load "dbe" )

dbe is loadded
sleep 5 did not work
Your suggested adjustements to .conkyrc seem to work! 
thnx for your help

---

### Post by lucksin on 2007-10-27
Thanks a ton...... i was going insane tring to figure out why emerald crashes everytime i load conky...

---

### Post by mazeman on 2008-02-26
Thanks. The change works for me too.

---

### Post by geekcliff on 2008-02-28
This worked for me too on gutsy:popcorn:

---

### Post by Wootyeah on 2008-06-20
Thanks a lot!  This saved my nerves in Hardy, too!

---

