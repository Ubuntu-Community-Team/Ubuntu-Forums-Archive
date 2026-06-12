---
title: "problem with 2nd conky panel"
date: 2011-02-09
forum: Desktop Environments
---

### Post by Arminius on 2011-02-09
the problem panel is on the right hand side of the attached photo

here is the code ```
#-----Run in Background
background yes
#-----Use XFT for Fonts
use_xft yes
xftfont TransponderAOE:size=32
xftalpha 0.5
#-----How often to run, in seconds
update_interval 1.0
#-----Window Controls, Has it's own, Normal, Transparent Window...
own_window yes
own_window_type normal
own_window_transparent yes
#-----...Undecorated, Sticky Window without putting it in the Taskbar or Pager, all Below everything else.
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#-----Text Buffer, how big a script can be when called.
text_buffer_size 2048
#-----Window Size and Width
minimum_size 350 10
maximum_width 400
#-----Stops the Blinking!
double_buffer yes
#-----Don't draw any shadows, shades, or outlines for the window or text.
draw_shades no
draw_outline no
draw_borders no
#-----DO draw borders around the graphs
draw_graph_borders yes
#-----Put the whole thing, bottom right.
alignment bottom_right
#-----Gap of 40 pixels between the Conky, and the edge of the screen, No gap at the top or bottom.
gap_x 0
gap_y -600
#-----Disables file system buffers from used memory
no_buffers yes
#-----How many samples to average for measuring CPU activity.
cpu_avg_samples 2
#---Dunno exactly, required for Weather section to work properly.
override_utf8_locale yes
#-----Helps keep certain things aligned.
use_spacer right

#-----Code shortcut for colours.
default_color 000000          #Black
color0 FF0000                 #Red
color1 FFFF00		              #Yellow
color2 FFFFFF                 #White
color3 808080                 #Grey
color4 00FF00									#Green
color5 C0C0C0									#Silver
color6 FFD700									#Gold
color7 0000FF									#Blue
color8 000080									#Navy


TEXT#-----This Entire Conky Script Is For a Clock.  Yes.  I Have Wasted an Entire Conky for this drivel.
${voffset -30}${font DiamondFantasy:size=16}${color6}${hr 2}${goto 150}${color2}Time ${color6}${hr 2}${color2}
#-----This is how to do a proper shadow hilight.
${font AGaramond:size=60}${color7}${offset -13}${goto 10}${time %l:%M:%S %p}
${voffset -95}${font AGaramond:size=60}${color0}${offset -15}${goto 10}${time %l:%M:%S %p}${font}
#-----Calendar by VinDSL (Version 3)
${goto 100}${execpi 60 date +'%B${offset 6}%Y'}${color6}${hr 1}${color2}
${voffset 25}${font TransponderAOE:bold:size=12}${color2}${alignc 135}${time %A}${font}
${voffset -40}${font TransponderAOE:bold:size=22}${color4}${alignc 135}${time %d}${font}
${voffset -40}${font TransponderAOE:bold:size=12}${color2}${alignc 135}${time %B}${font}
${voffset -60}${font TransponderAOE:bold:size=12}${color2}${alignc 135}${time %Y}${font}
${voffset -175}${font TransponderAOE:bold:size=14}${color7}${execpi 1800 cal | sed '1d' | sed s/^/"\$\{offset 140"\}/ | sed '/^ *$/d' | sed 's/\<'"$(date +%-d)"'\>/${color0}&${color7}/'}${font}
${voffset -212}${font TransponderAOE:bold:size=14}${color0}${execpi 1800 cal | sed '1d' | sed s/^/"\$\{offset 140"\}/ | sed '/^ *$/d' | sed 's/\<'"$(date +%-d)"'\>/${color1}&${color0}/'}${font}
```

I have told it to go for the bottom right of the screen, but it takes up that entire side. how do I tell it to stay in the bottom right only?

---

