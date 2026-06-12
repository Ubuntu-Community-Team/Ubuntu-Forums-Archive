---
title: "Conky: no background transparency"
date: 2013-10-18
forum: Desktop Environments
---

### Post by manoriax on 2013-10-18
Hello!
Here's a question about Conky. I freshly installed Ubuntu 13.10 yesterday and wanted to use my old .conkyrc file only to find out that it messes up the background of the conky window. It is black instead of transparent. Does anybody know how I could fix that?

Here is my conkyrc:

```
# 
background no
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 1
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes

maximum_width 500
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color lightgray
default_shade_color red
default_outline_color green
alignment top_right
gap_x 24
gap_y 24

no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale yes
use_spacer none

TEXT
# SYS
${font Open Sans:Bold:size=10}${color gray99}SYSTEM${hr 2}$color${font}
$sysname $kernel $alignr $machine
Uptime $alignr $uptime

# CPU
${font Open Sans:Bold:size=10}${color gray99}CPU${hr 2}
$color${font}AMD A6-3420M $alignr ${freq_g cpu0}GHz
$stippled_hr
${font}Core 0 @ ${cpu cpu1} % $alignc ${color gray99}${cpubar cpu1}${color}
${font}Core 1 @ ${cpu cpu2} % $alignc ${color gray99}${cpubar cpu2}${color}
${font}Core 2 @ ${cpu cpu3} % $alignc ${color gray99}${cpubar cpu3}${color}
${font}Core 3 @ ${cpu cpu4} % $alignc ${color gray99}${cpubar cpu4}${color}

# TOP
${font Open Sans:Bold:size=10}${color gray99}TOP${hr 2}
$color${font}${font Open Sans:bold:size=8.5}PROCESS $alignr CPU USAGE$font
${top name 1}${alignr}${top cpu 1} % ${hr 2}
${top name 2}${alignr}${top cpu 2} %
${top name 3}${alignr}${top cpu 3} %
${top name 4}${alignr}${top cpu 4} %
${top name 5}${alignr}${top cpu 5} %

# Speicher
${font Open Sans:Bold:size=10}${color gray99}Memory${hr 2}
$color${font}${font Open Sans:bold:size=8.5}RAM$font
$mem / $memmax $alignr $memperc %
$membar

${font Open Sans:bold:size=8.5}SWAP$font
$swap / $swapmax $alignr $swapperc
${swapbar};

# HDD
${font Open Sans:Bold:size=10}${color gray99}HDD${hr 2}

${font Open Sans:bold:size=8.5}ROOT $font$font$alignr ${fs_type /}
${fs_used /} / ${fs_size /} $alignr ${fs_used_perc /} %
${fs_bar /}

# Netzwerk
${font Open Sans:Bold:size=10}${color gray99}Network${hr 2}
${font Open Sans:bold:size=8.5}eth0
${font} IPv4 ${alignr}${addr eth0}
${font} Down ${alignr}${downspeed eth0}
${font} Up ${alignr}${upspeed eth0}
${font}Total down ${alignr}${totaldown eth0}
${font}Total up ${alignr}${totalup eth0}
$stippled_hr
${font Open Sans:bold:size=8.5}wlan0
${font} IPv4 ${alignr}${addr wlan0}
${font} Down ${alignr}${downspeed wlan0}
${font} Up ${alignr}${upspeed wlan0}
${font} Total down ${alignr}${totaldown wlan0}
${font} Total up ${alignr}${totalup wlan0}
$stippled_hr
${font} IPv4 (WAN) ${alignr}${execi 7200 ~/.conky/publicip.sh}
```

File management is done by Nemo (not Nautilus), the desktop manager I use is gdm (not lightdm) and desktop environment is Gnome 3 with gnome-shell enabled.

Thanks in advance!

-Phil

---

### Post by stinkeye on 2013-10-18
This is usually caused by compositing not being enabled in your window manager.
Install wmctrl to easily determine your window manager....
```
sudo apt-get install wmctrl
```

Then run this to show current session and window manager...
```
echo $DESKTOP_SESSION && wmctrl -m | head -n1
```
eg my output...
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **echo $DESKTOP_SESSION && wmctrl -m | head -n1**
ubuntu
Name: Compiz
```

I don't use gnome-shell so can't test or advise on what you need to do.
Your config draws a transparent window for me in 13.04 Unity with compiz as the window manager.

Your current gfx driver may also be a factor...
```
lspci -nnk | grep -iA2 vga
```


In your conky config try different settings.
eg **override** windows are not controlled by the window manager and ignore **own_window_hints**
```
own_window_type [COLOR="#FF0000"]override[/COLOR]
```


Try ARGB real transparency.
Does not work with **own_window_type override**

eg try these settings
```
own_window_type **normal**
own_window_transparent no
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_argb_visual yes
own_window_argb_value 0
```

When using **own_window_argb_visual yes** with **own_window_transparent no**
you can determine the transparency of the window with the **own_window_argb_value** setting.
ie
**own_window_argb_value 0** ........... fully transparent
**own_window_argb_value 255** ........ fully opaque

_own_window_argb_value [COLOR="#FF0000"]0[/COLOR]_
[ATTACH=CONFIG]247043[/ATTACH]


_own_window_argb_value [COLOR="#FF0000"]180[/COLOR]_
[ATTACH=CONFIG]247044[/ATTACH]

_own_window_argb_value [COLOR="#FF0000"]255[/COLOR]_
[ATTACH=CONFIG]247045[/ATTACH]

When making config changes it's a good idea to kill conky and reload.
After a config change hit alt+F2 and run.....
```
killall -SIGUSR1 conky
```

---

### Post by manoriax on 2013-10-19
```
own_window_type normal
own_window_transparent no
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_argb_visual yes
own_window_argb_value 0
```

Did the trick, thank you!

---

