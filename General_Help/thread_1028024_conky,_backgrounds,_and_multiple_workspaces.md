---
title: "conky, backgrounds, and multiple workspaces"
date: 2009-01-02
forum: General Help
---

### Post by blampars on 2009-01-02
i've setup my desktop with compiz cube to have 3 workspaces, all with their own backgrounds.
i'm running conky, transparent.
when i switch workspaces, conky keeps the background of the first workspace. is there any way that i can make it so it uses transparency for all 3 backgrounds instead of just the first one?
[_picture here_]("http://tricky.bluesphereweb.com/conkyprobs.png")

i've been playing around with it, but havnt been able to figure out a solution.

-b

---

### Post by loomsen on 2009-01-02
Been strugglin with this problem a lot as well. No solution yet, at least not a practicable one.

But there are patches for nautilus to make it draw different backgrounds, should work with conky as well then. 

Search google for patches nautilus different backgrounds or so.

---

### Post by blampars on 2009-01-02
a buddy just suggested the following..
> 01:31 <~MPIIIMan> hmm, maybe you can specify a specific background for it to use
01:31 <~MPIIIMan> like a PNG
01:31 <~MPIIIMan> then just create a fake transparent PNG in GIMP

is it possible to specify an image for conky to use as background?

---

### Post by loomsen on 2009-01-02
Tried this as well, doesn't work with conky.

You could get the greenscreen plugin for compiz and set the background to hotpink or so, and then specify hotpink to be transparent in compiz-greenscreen. But I dont know if this will work properly.

Try and post your findings please, havent been using conky for a while now cause this kinda sucked. 

If you find a proper solution, pls let us know.

Another way is to make conky half transparent or so in compiz, this way it would at least melt in somewhat better with your desktop. I found setting opacity to 40-50%, conky background to black and chosing dark wallpapers worked well. But it's a very workaroundish solution...

---

### Post by tturrisi on 2009-01-02
post your .conkyrc

---

### Post by blampars on 2009-01-02
ok, worked on this for hours last night and for another two today.  it doesnt seem i'm going to get any sort of cooperation out of conky and compiz. [-(

setting black background on conky and messing with settings in compiz gave me no visible changes that I could see. window rules, widget layers, and opacity settings in general options had no effect.

here is my conkyrc as requested, in the last state i left it after playing with things..

```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 185 0
#maximum_width 200

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
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color black
#default_outline_color grey
#own_window_colour black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 20
gap_y 130

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

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
SYSTEM ${hr 2}
${alignc}smile, breathe and go slowly
${voffset 2}${font openlogos:size=16}u${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,60}
${font StyleBats:size=16}A${font}   CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,60}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 17}${font Arial Black:size=16}${time %H:%M}${font}
${alignc}${time %A %d %B %Y}

HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Root:
${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:
${voffset 4}${fs_used /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}

NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PIZZADUDEBULLETS:size=14}O${font}   Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 BEBEBE BEBEBE}
${voffset 4}${font PIZZADUDEBULLETS:size=14}U${font}   Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 BEBEBE BEBEBE}
${voffset 4}${font PIZZADUDEBULLETS:size=14}N${font}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PIZZADUDEBULLETS:size=14}T${font}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PIZZADUDEBULLETS:size=14}Z${font}   Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PIZZADUDEBULLETS:size=14}a${font}   Local Ip: ${alignr}${addr wlan0}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PIZZADUDEBULLETS:size=14}O${font}   Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 789E2D A7CC5C}
${voffset 4}${font PIZZADUDEBULLETS:size=14}U${font}   Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 789E2D A7CC5C}
${voffset 4}${font PIZZADUDEBULLETS:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PIZZADUDEBULLETS:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PIZZADUDEBULLETS:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PIZZADUDEBULLETS:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 789E2D A7CC5C}
${voffset 4}${font PIZZADUDEBULLETS:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 789E2D A7CC5C}
${voffset 4}${font PIZZADUDEBULLETS:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PIZZADUDEBULLETS:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PIZZADUDEBULLETS:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
${endif}${else}
${font PIZZADUDEBULLETS:size=14}4${font}   Network Unavailable
${endif}
```

---

