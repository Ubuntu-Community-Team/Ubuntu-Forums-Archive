---
title: "conky wont's display fonts"
date: 2009-01-11
forum: General Help
---

### Post by draze on 2009-01-11
~/.conkyrc
```
background yes
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 180 5
maximum_width 300
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color greenbackground yes
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 180 5
maximum_width 300
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 10
gap_y 10
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes

TEXT
${color white}${font Arial:size=30}$alignc${time %H:%M}
${voffset -30}${font Arial:bold:size=10}$alignc${time %d %b %Y}
${font Arial:bold:size=8}$alignc${time %A}


${font Arial:bold:size=10}${color white}${hr 1}
${font Verdana:bold:size=8}${color white}CPU $alignr${cpu cpu}%
${font Arial:bold:size=8}${color white}RAM $alignr $memperc%
SWP $alignr $swapperc%
UPT $alignr${uptime}
${font Arial:bold:size=10}${color white}${hr 1}
${font Arial:bold:size=8}${color white}Down$alignr${downspeed eth1}kb/s
Up$alignr${upspeed eth1}kb/s
Download${alignr}${totaldown eth1}
${font DejaVuSans-Bold:bold:size=8}${color white}Upload ${alignr}${totalup eth1}
alignment top_right
gap_x 10
gap_y 10
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes

TEXT
${color white}${font Arial:size=30}$alignc${time %H:%M}
${voffset -30}${font Arial:bold:size=10}$alignc${time %d %b %Y}
${font Arial:bold:size=8}$alignc${time %A}


${font Arial:bold:size=10}${color white}${hr 1}
${font Verdana:bold:size=8}${color white}CPU $alignr${cpu cpu}%
${font Arial:bold:size=8}${color white}RAM $alignr $memperc%
SWP $alignr $swapperc%
UPT $alignr${uptime}
${font Arial:bold:size=10}${color white}${hr 1}
${font Arial:bold:size=8}${color white}Down$alignr${downspeed eth1}kb/s
Up$alignr${upspeed eth1}kb/s
Download${alignr}${totaldown eth1}
${font DejaVuSans-Bold:bold:size=8}${color white}Upload ${alignr}${totalup eth1}
```

[IMG]http://www.loadyourimage.com/images/720_2009_01_10_1231644238_1024x768.png[/IMG]

I'm using Crunchbang linux 8.04 lite and can't get my conky dispay fonts. I tried Arial, Verdana, DejaVu, Dotmatrix, Weather. None of them I was able to display in conky.

ls -al .fonts
```
total 492
drwxr-xr-x  2 draze draze   4096 2009-01-10 11:37 .
drwxr-xr-x 33 draze draze   4096 2009-01-10 14:37 ..
-rw-r--r--  1 draze draze  88360 1992-03-13 06:27 Dotmatrx.ttf
-rw-r--r--  1 draze draze  56196 2008-11-25 15:24 Found_receipt_demo.ttf
-rw-rw-rw-  1 draze draze    731 2000-10-31 16:22 other_prophits.txt
-rw-r--r--  1 draze draze  49224 2004-10-17 11:38 V5PRC___.TTF
-rw-r--r--  1 draze draze 126016 2004-10-17 11:38 V5PRD___.TTF
-rw-r--r--  1 draze draze 113180 2004-10-17 11:38 V5PRF___.TTF
-rw-r--r--  1 draze draze  26860 2007-02-09 14:15 weather.ttf
```

cd .fonts
sudo cp *.ttf /usr/share/fonts/truetype
sudo fc-cache -f -v
```
draze@draze-laptop:~$ cd .fonts
draze@draze-laptop:~/.fonts$ sudo cp *.ttf /usr/share/fonts/truetype
sudo: unable to resolve host draze-laptop
draze@draze-laptop:~/.fonts$ sudo fc-cache -f -v
sudo: unable to resolve host draze-laptop
/usr/share/fonts: caching, new cache contents: 0 fonts, 3 dirs
/usr/share/fonts/X11: caching, new cache contents: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: caching, new cache contents: 8 fonts, 0 dirs
/usr/share/fonts/X11/encodings: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: caching, new cache contents: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 3 fonts, 3 dirs
/usr/share/fonts/truetype/freefont: caching, new cache contents: 12 fonts, 0 dirs
/usr/share/fonts/truetype/msttcorefonts: caching, new cache contents: 60 fonts, 0 dirs
/usr/share/fonts/truetype/ttf-dejavu: caching, new cache contents: 21 fonts, 0 dirs
/usr/share/fonts/type1: caching, new cache contents: 0 fonts, 1 dirs
/usr/share/fonts/type1/gsfonts: caching, new cache contents: 35 fonts, 0 dirs
/usr/share/X11/fonts: skipping, no such directory
/usr/local/share/fonts: caching, new cache contents: 0 fonts, 0 dirs
/home/draze/.fonts: caching, new cache contents: 6 fonts, 0 dirs
/var/cache/fontconfig: cleaning cache directory
/home/draze/.fontconfig: cleaning cache directory
fc-cache: succeeded
draze@draze-laptop:~/.fonts$ 
```


Help.

---

### Post by draze on 2009-01-12
up

---

### Post by easybake on 2009-01-12
What are the errors when you run conky from terminal?

---

