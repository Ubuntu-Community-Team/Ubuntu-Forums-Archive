---
title: "Bottom of conky window suddenly cut off"
date: 2009-02-22
forum: General Help
---

### Post by yonexFactory on 2009-02-22
I have not changed my .conkyrc file at all (posted below), but for some reason, the bottom of my conky window is now cut off and I can't figure out why. Anyone know what could be the cause?

Before:
[IMG]http://i196.photobucket.com/albums/aa81/yonexFactory/Screenshot-1-1.png[/IMG]

Now:
[IMG]http://i196.photobucket.com/albums/aa81/yonexFactory/Screenshot-2-1.png[/IMG]

.conkyrc:
```
cpu_avg_samples 2
net_avg_samples 2
top_cpu_separate no
out_to_console no
update_interval 0.5
total_run_times 0
background yes

# FONT
use_xft yes
override_utf8_locale yes
xftfont DejaVu Sans:style=Bold:size=8
xftalpha 0.8
uppercase no


# FORMAT
alignment top_right
gap_x 0
gap_y 0

draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
stippled_borders 0
border_margin 6
border_width 0

use_spacer none
maximum_width 250
minimum_size 100 788
short_units yes

# WINDOW
own_window yes
own_window_type normal
own_window_title colorconky
own_window_transparent no
own_window_hints undecoratedbelow,sticky,skip_taskbar,skip_pager
own_window_colour black

# BUFFERS
no_buffers yes
double_buffer yes
text_buffer_size 2048

# COLORS
default_color white
color1 white
#default_shade_color white
#default_outline_color 01040d

TEXT
${offset -5}${voffset -12}${font DejaVu Sans Mono:size=72}${time %H}
${offset 129}${voffset -155}${font DejaVu Sans Mono:size=30}${time %M:%S}
${offset 131}${voffset -25}${font DejaVu Sans Mono:size=14}${time %b}
${offset 132}${voffset -5}${time %d}
${color 6b6b6b}${font DejaVu Sans Mono:size=12}${execpi 60 DJS=`date +%_d`; cal | sed '1d' | sed '/./!d' | sed 's/$/                     /' | fold -w 21 | sed -n '/^.\{21\}/p' | sed 's/^/${alignc} /' | sed /" $DJS "/s/" $DJS "/" "'${color1}'"$DJS"'${color1}'" "/}
${font OpenLogos:style=normal:size=12}u ${voffset -2}${font DejaVu Sans Mono:style=Bold:size=11}System$font  $hr
${alignr}$uptime_short
CPU:  ${goto 45}${cpu cpu1}% ${goto 90}${cpubar cpu1}
RAM:  ${goto 45}$memperc%    ${goto 90}$membar
Swap: ${goto 45}$swapperc%   ${goto 90}$swapbar

CPU               ${goto 117}PID              ${goto 160}CPU%             ${goto 205}MEM%
${top name 1}     ${goto 110}${top pid 1}     ${goto 155}${top cpu 1}     ${goto 200}${top mem 1}
${top name 2}     ${goto 110}${top pid 2}     ${goto 155}${top cpu 2}     ${goto 200}${top mem 2}
${top name 3}     ${goto 110}${top pid 3}     ${goto 155}${top cpu 3}     ${goto 200}${top mem 3}

Memory
${top_mem name 1} ${goto 110}${top_mem pid 1} ${goto 155}${top_mem cpu 1} ${goto 200}${top_mem mem 1}
${top_mem name 2} ${goto 110}${top_mem pid 2} ${goto 155}${top_mem cpu 2} ${goto 200}${top_mem mem 2}
${top_mem name 3} ${goto 110}${top_mem pid 3} ${goto 155}${top_mem cpu 3} ${goto 200}${top_mem mem 3}

Root     ${if_mounted /} ${goto 60}${fs_used_perc /}%   ${fs_free /} / ${fs_size /} ${goto 200}${fs_bar /} $else${color 4C4039}${goto 60}Not Mounted$color$endif
Stuff    ${if_mounted /media/Local\040Disk} ${goto 60}${fs_used_perc /media/Lois}%   ${fs_free /media/Lois} / ${fs_size /media/Lois}${goto 200}${fs_bar /media/Lois} $else${color 4C4039}${goto 60}Not Mounted$color$endif
Fred     ${if_mounted /media/FreeAgent\040Drive}   ${goto 60}${fs_used_perc /media/Fred}%   ${fs_free /media/Fred} / ${fs_size /media/Fred}${goto 200}${fs_bar /media/Fred} $else${color 4C4039}${goto 60}Not Mounted$color$endif

Interweb
Down: ${downspeed eth0} k/s                 ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,110 000000 000000} ${alignr}${upspeedgraph eth0 25,110 000000 000000}
Total: ${totaldown eth0}                    ${alignr}Total: ${totalup eth0}

${font ConkyWeather:style=Normal:size=12}o $font${voffset -2}${font DejaVu Sans Mono:style=Bold:size=11}Weather$font  $hr

${execpi 180 conkyForecast --location=USMN0429 --template=/home/nick/.conky-forecast}
${voffset -45}${font OpenLogos:style=normal:size=144}v
```

---

### Post by easybake on 2009-02-22
voffsets can sometimes be an issue. Sometimes you can simply add extra blank lines to the end of the conkyrc. Just hit enter like 8 times at the bottom.

---

### Post by yonexFactory on 2009-02-22
> **easybake said:**
> voffsets can sometimes be an issue. Sometimes you can simply add extra blank lines to the end of the conkyrc. Just hit enter like 8 times at the bottom.

Whoa, thanks for the speedy reply... but unfortunately this did not work. In fact, if I change the end to ```
${execpi 180 conkyForecast --location=USMN0429 --template=/home/nick/.conky-forecast}
1
2
3
4
5
${voffset -45}${font OpenLogos:style=normal:size=144}v
``` then all I can see is the 1 and one row of pixels from the 2. I've also tried changing some values here and there at the beginning, but to no avail.

---

### Post by easybake on 2009-02-22
I meant to do the spaces after the last variable line.

blahblahblah
1
2
3
4
5

---

### Post by yonexFactory on 2009-02-22
Yep, that's what I tried, I was just saying that neither spaces nor text seem to change how far down the window actually goes... it's always just one line plus a couple pixels past the weather forcast.

---

### Post by yonexFactory on 2009-02-23
I figured out if I have own_window set to no instead of yes, the bottom does not get cut off... but I would prefer to have it in its own window...

Edit: it also works if I set own_window_type to override and keep own_window set to yes. But in either case, I can't use Devilspie to create transparency. So I guess I'll just change my wallpaper for now...

---

### Post by smistad on 2009-08-23
I had the same problem. I fixed it by editing this line in the ~/.conkyrc file:
```
minimum_size 182 0
```The first number is the minimum width and the second number is the minimum height. I fixed the problem by simply setting the minimum height to the number of pixel it needed like this:
```
minimum_size 182 700
```

---

### Post by Shpongle on 2009-09-14
> **smistad said:**
> I had the same problem. I fixed it by editing this line in the ~/.conkyrc file:
```
minimum_size 182 0
```The first number is the minimum width and the second number is the minimum height. I fixed the problem by simply setting the minimum height to the number of pixel it needed like this:
```
minimum_size 182 700
```

thanks man that fixed it for me

---

