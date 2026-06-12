---
title: "Conky 9.04 Script Problem (9.04 added border)"
date: 2009-04-26
forum: General Help
---

### Post by JohnSearle on 2009-04-26
Conky is adding a light border around itself. I didn't have this problem in previous versions of Ubuntu, and I'm using the same script.

Any thoughts?

```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 250 5

maximum_width 250

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 0

# Default colors and also border colors
default_color 1E1C1A
#default_shade_color white
#default_outline_color 1E1C1A
own_window_colour 1E1C1A

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 30

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
override_utf8_locale yes

# Add spaces to keep things from moving about? This only affects certain objects.
use_spacer none

#If you want a Gmail notify, put the this parameter after the line "${font PizzaDude Bullets:size=14}b${font} Public Ip: $alignr${execi 1 ~/.scripts/ip.sh}" in all 3 cases, whithout "#" and replace user password.
#${font FreeSans:size=14}@${font}${execpi 300 python ~/.scripts/gmail_parser.py user password 3}

TEXT
SYSTEM ${hr 2}
${font OpenLogos:size=16}u${font} Kernel: ${alignr}${kernel}
${font StyleBats:size=16}A${font} CPU 1: ${cpu cpu1}% ${alignr}${cpubar 8,120 cpu1}
${font StyleBats:size=16}A${font} CPU 2: ${cpu cpu2}% ${alignr}${cpubar 8,120 cpu2}
${font StyleBats:size=16}A${font} CPU AVG: ${cpu cpu0}% ${alignr}${cpubar 8,120 cpu0}
${font StyleBats:size=16}g${font} RAM: $memperc% ${alignr}${membar 8,120}
${font StyleBats:size=16}j${font} SWAP: $swapperc% ${alignr}${swapbar 8,120}
${font StyleBats:size=16}q${font} On: ${alignr}${uptime}
--------------------------------
Processes: $processes Run: $running_processes
--------------------------------
DATE ${hr 2}
${font Arial Black:size=26}${time %I:%M %P}${font}
${voffset 6}${alignc}${time %A %d %Y}
HD ${hr 2}
${font PizzaDude Bullets:size=14}g${font} Root:
${fs_used /}/${fs_size /} $alignr${fs_bar 8,120 /}
${font PizzaDude Bullets:size=14}g${font} USB Drive:
${fs_type /media/USB DRIVE} ${alignr}${fs_bar 8,120 /media/USB DRIVE}

NETWORK ${hr 2}
${font PizzaDude Bullets:size=14}v${font} Up:  ${upspeed eth0} kb/s $alignr${upspeedgraph eth0 8,120 789E2D A7CC5C}
${font PizzaDude Bullets:size=14}r${font} Down:  ${downspeed eth0} kb/s $alignr${downspeedgraph eth0 8,120 789E2D A7CC5C}
${font PizzaDude Bullets:size=14}N${font} Upload: $alignr${totalup eth0}
${font PizzaDude Bullets:size=14}T${font} Download: $alignr${totaldown eth0}

GMAIL ${hr 2}
${font}${texeci 60 perl ~/scripts/gmail.pl n} ${color}new message(s) 
```

---

### Post by linuxuser21 on 2009-04-26
Does this just happen on startup? I've noticed a quite a bit of problems with it & this happens to be one of them.  Does it help to restart it (killing it & then starting it back up)?

---

### Post by wsonar on 2009-04-26
I think this can be fixed by going to system /preferences /compiz manager

window decorations

turn the shadow opacity part all the way down

---

### Post by JohnSearle on 2009-04-26
> **linuxuser21 said:**
> Does this just happen on startup? I've noticed a quite a bi of problems with it & this happens to be one of them.  Does it help to restart it (killing it & then starting it back up)?

Yup, that seems to be the issue with mine. If I close it and restart, then it seems fine.

Also, I found that if I turn off all the compiz effects, then it seems fine, and if I turn them back on, it adds the shadow.

> **wsonar said:**
> I think this can be fixed by going to system /preferences /compiz manager

window decorations

turn the shadow opacity part all the way down

Not entirely sure where you found those options. I have CompizConfig Settings Manager installed, under which I can't locate the option.

- John

---

### Post by wsonar on 2009-04-26
> **JohnSearle said:**
> 


Not entirely sure where you found those options. I have CompizConfig Settings Manager installed, under which I can't locate the option.

- John

effects /windows decoratins

---

### Post by linuxuser21 on 2009-04-26
If you want a quick way to restart it, I've created 2 Conky buttons on my dock (works as a launcher on the desktop as well).
For the panel: right click on panel> Add to panel> Custom Application Launcher.  Name it Conky (or whatever you want) and for the Command:
One to kill Conky:
```
killall conky
```
One to start conky:
```
conky
```
It is annoying to have to do this on every startup; however, it's what I've come up with.

---

### Post by VCoolio on 2009-04-26
If you use compiz you can disable the shadows on conky with the window decorations plugin. In the shadows entry make it:
any & !(class=conky)

If you don't want shadows on the panel (because the shadow covers a part of window title bars) add !(class=gnome-panel). And so on, add anything you want.

---

### Post by altonbr on 2009-08-08
> **VCoolio said:**
> If you use compiz you can disable the shadows on conky with the window decorations plugin. In the shadows entry make it:
any & !(class=conky)

If you don't want shadows on the panel (because the shadow covers a part of window title bars) add !(class=gnome-panel). And so on, add anything you want.

I can't seem to get that to work after killing and restarting conky.

---

### Post by altonbr on 2009-08-08
I found you can fix the conky/border shadow issue in compiz by going to 'Window Decorations' and use
```
any, !conky
```
for 'Shadow windows'. 'Decoration windows' can stay as 'any'.

You should be able to see this work automatically (e.g. if you screw up the input, all your borders will disappear. If you forget what the default was, it's 'any' for both 'Shadow windows' and 'Decoration windows')

---

### Post by cake nom nom on 2009-08-30
> **wsonar said:**
> I think this can be fixed by going to system /preferences /compiz manager

window decorations

turn the shadow opacity part all the way down

that fixed mine thanks

---

### Post by bullium on 2009-12-21
> **VCoolio said:**
> If you use compiz you can disable the shadows on conky with the window decorations plugin. In the shadows entry make it:
any & !(class=conky)

If you don't want shadows on the panel (because the shadow covers a part of window title bars) add !(class=gnome-panel). And so on, add anything you want.

Running Karmic and this solution worked great for me.

---

