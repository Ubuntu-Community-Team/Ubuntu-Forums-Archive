---
title: "Conky won't display todo.txt correctly"
date: 2011-03-16
forum: Desktop Environments
---

### Post by zookrider on 2011-03-16
I'm trying to display my todo.txt file in my Conky, but it won't align correctly. Only the first line of the list is where I want it, the rest is in the default location.

> background yes
update_interval 1

cpu_avg_samples 2
net_avg_samples 2
temperature_unit celsius

double_buffer yes
no_buffers yes
text_buffer_size 2048

gap_x 1100
gap_y 30
minimum_size 190 450
maximum_width 190
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
border_inner_margin 0
border_outer_margin 0
alignment top_right

draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

override_utf8_locale yes
use_xft yes
xftfont caviar dreams:size=8
xftalpha 0.5
uppercase no

default_color 666666
color1 888888
color2 AAAAAA
color3 DDDDDD
color4 CC3333

lua_load ~/Conky/conky_red/conky_red.lua
lua_draw_hook_post main

TEXT
${voffset 35}
${goto 95}${color4}${font ubuntu:size=22}${time %e}${color1}${offset -50}${font ubuntu:size=10}${time %A}
${goto 85}${color2}${voffset -2}${font ubuntu:size=9}${time %b}${voffset -2} ${color3}${font ubuntu:size=12}${time %Y}${font}

${voffset 80}
${goto 90}${font Ubuntu:size=7,weight:bold}${color}CPU
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${top name 1}${alignr}${top cpu 1}%
${goto 90}${font Ubuntu:size=7,weight:normal}${color2}${top name 2}${alignr}${top cpu 2}%
${goto 90}${font Ubuntu:size=7,weight:normal}${color3}${top name 3}${alignr}${top cpu 3}%
${goto 90}${cpugraph 10,100 AAAAAA AAAAAA}
${goto 90}${voffset -10}${font Ubuntu:size=7,weight:normal}${color}${threads} process 

${voffset 20}
${goto 90}${font Ubuntu:size=7,weight:bold}${color}MEM
${goto 90}${font Ubuntu:size=7,weight:normal}${color1}${top_mem name 1}${alignr}${top_mem mem 1}%
${goto 90}${font Ubuntu:size=7,weight:normal}${color2}${top_mem name 2}${alignr}${top_mem mem 2}%
${goto 90}${font Ubuntu:size=7,weight:normal}${color3}${top_mem name 3}${alignr}${top_mem mem 3}%

${voffset 20}
${goto 90}${font Ubuntu:size=7,weight:bold}${color}DISKS

${goto 90}${diskiograph 30,100 AAAAAA AAAAAA}${voffset -30}
${goto 90}${font Ubuntu:size=7,weight:normal}${color}used: ${fs_used /home} /home
${goto 90}${font Ubuntu:size=7,weight:normal}${color}used: ${fs_used /} /

${voffset 1}
${goto 20}${font Ubuntu:size=7,weight:bold}${color}EXAILE
${goto 20}${font Ubuntu:size=7,weight:normal}${color}${execp conkyExaile --template=~/Conky/conkyExaile.template}

${voffset 0}
${goto 20}${font Ubuntu:size=7,weight:bold}${color}TO DO
${goto 20}${font Ubuntu:size=7,weight:bold}${color}${execpi 60 todo.sh -p ls}

This results in an output that roughly looks like this (the ellipses are just place holders):
> 
..........TO DO
..........1 Task one
..2 Task two
..3 Task three
..4 Task four

Any idea how to get the whole list to line up correctly?

---

### Post by zookrider on 2011-03-16
Never mind, I fixed it by using a modified version of Kaivalagi's conkyText script.

Edit: I thought I fixed it but Kaivalagi's script doesn't allow the functionality of the todo.sh (such as sorting by priority).
Still looking for a solution.

---

### Post by zookrider on 2011-03-16
OK, a guy on here had a similar problem, he was trying to get a text file to align right but only the first line would cooperate. He solved it with the following:

> ${execpi 30 cat /home/andrew/.scripts/todo | sed s/^/\${alignr}/ }

So I tried to apply his lesson and did this:

> ${excecpi 60 todo.sh -p ls | sed s/^/\${goto 20}/}

This resulted in the text disappearing altogether. No dice. Am I on the right track?

---

### Post by zookrider on 2011-03-16
Tried replacing goto with offset in both the original configuration and the one listed in post 3. Same results as with goto. Also used alignr with sed (post 3), that worked, alignl however:
> ${font Ubuntu:size=7,weight:bold}${color}${execpi 30 todo.sh -p ls | sed s/^/\${alignl}/ }
caused the following:
> {alignl}1 A Task One
{alignl}2 A Task Two
{alignl}3 A Task Three

---

### Post by zookrider on 2011-03-17
HELLO HEllo helloo...
IS ANYBODY HERE HEre here...

Am I in the wrong forum? I just showered so I know I don't smell funny. Seriously this is the second thread in a row I started here looking for help where I didn't get a single reply. Did I do something wrong?

---

### Post by stinkeye on 2011-03-17
> ${voffset 0}
${goto 20}${font Ubuntu:size=7,weight:bold}${color}TO DO
**${goto 20}**${font Ubuntu:size=7,weight:bold}${color}${execpi 60 todo.sh -p ls}
How  does it look if you remove the **${goto 20}**

---

### Post by zookrider on 2011-03-17
Like this:

> ..........TO DO
1 A Task One
2 B Task Two
3 C Task Three

TODO: 3 of 3 tasks shown

Only the left portion is cut off by the edge of the screen, the numbers and the "TO" in "TODO". Again the ellipses are just place holders.

Also, figured out that alignl is not an actual conky output command so that explains that.

---

### Post by stinkeye on 2011-03-17
The only way I know how to fix is not to precede the todo script with a
${goto} and fix up the rest of the ${goto}s and settings to match.

Also, in your config you have...
```
alignment top_right
gap_x 1100
```
which means your starting your conky at the top right and pushing it
1100 pixels to the left which may not suit your screen size and cut off the first part of your conky.

What's wrong with using...
```
alignment top_left
gap_x 10
```

---

### Post by zookrider on 2011-03-17
> **stinkeye said:**
> 
Also, in your config you have...
```
alignment top_right
gap_x 1100
```
which means your starting your conky at the top right and pushing it
1100 pixels to the left which may not suit your screen size and cut off the first part of your conky.

What's wrong with using...
```
alignment top_left
gap_x 10
```

You nailed it. This is a script I found on the web and was trying to modify for my use. I'm not sure why the original author chose to write it that way but using a top_left alignment solved the problem. Thank you very much for your help.

---

