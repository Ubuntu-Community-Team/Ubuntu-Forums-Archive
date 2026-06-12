---
title: "Conky shows LightDM background instead of Xfce desktop"
date: 2011-10-22
forum: Desktop Environments
---

### Post by Zercius on 2011-10-22
This is a bit of a weird issue. When starting Conky on Xubuntu 11.10, the background shows LightDM instead of the Xfce desktop. It does not matter when I start Conky; even after having logged in for several minutes conky will still display the LightDM background when started.

Here is my conkyrc file (header omitted):
```
alignment bottom_right
background yes
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont Sawasdee:size=16
gap_x 5
gap_y 20
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_type desktop
own_window_transparent yes
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no
format_human_readable yes
double_buffer yes

lua_load ~/Projects/Scripts/draw_bg.lua
lua_draw_hook_pre draw_bg

TEXT
${outlinecolor #888888}${font Sawasdee:size=50}${time %I:%M %P}$font
${font Sawasdee:size=20}${time %A, %e %B %Y}$font${if_existing /proc/acpi/battery/BAT0}
${font Sawasdee:bold:size=16}Battery:$font $battery_percent%, $battery_time${endif}${if_up wlan0}
${font Sawasdee:bold:size=16}Wireless: $font${wireless_essid wlan0} ${wireless_link_qual_perc wlan0}%${endif}
${font Sawasdee:bold:size=16}CPU:$font $cpu%${font Sawasdee:size=12}
${top cpu 1}% ${top name 1}
${top cpu 2}% ${top name 2}

```


I also tried changing own_window_type between "override" and "desktop" modes; both behave the same.

---

### Post by Shazaam on 2011-10-22
[http://ubuntuforums.org/showthread.php?t=1049693](http://ubuntuforums.org/showthread.php?t=1049693)

Might help.

---

### Post by Zercius on 2011-10-22
Yeah, I already do that. It doesn't matter how long I wait; conky still shows the wrong background if started minutes or even hours after login.

---

### Post by gsmanners on 2011-10-22
[http://ubuntuforums.org/showthread.php?t=1861153](http://ubuntuforums.org/showthread.php?t=1861153)

This one might help (might not, but what the heck).

---

### Post by stinkeye on 2011-10-22
Try 
```
own_window_type **normal**
```

---

### Post by Toz on 2011-10-22
> **gsmanners said:**
> [http://ubuntuforums.org/showthread.php?t=1861153](http://ubuntuforums.org/showthread.php?t=1861153)

This one might help (might not, but what the heck).

+1.
Add:
```
own_window_argb_visual yes
own_window_argb_value 0
```
You need to have the compositor enabled for them to work.

---

### Post by Zercius on 2011-10-23
Thanks guys, ARGB visual did it (and yes, I have the compositor enabled). 

own_window_type_normal actually draws window frames around Conky, which is not what I wanted.

---

### Post by pixel_1001 on 2012-01-21
Thanks Toz! your answer was helpful for me!

---

### Post by Sector11 on 2012-01-21
> **Zercius said:**
> Thanks guys, ARGB visual did it (and yes, I have the compositor enabled). 

own_window_type_normal actually draws window frames around Conky, which is not what I wanted.

From the #! Forums, I don't use Xfce:

[quote=VastOne]These are my settings in conky for transparency with Xfce 
```
draw_borders no
own_window_argb_visual yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window yes
own_window_transparent yes
own_window_class conky-semi
```

If I do not enable compositing, I have a black box background

I do not use Cairo Compositing, I use xcompmgr, which is the #! default

On several machines I am responsible for, these are the same settings ... I have never seen or known of any issues with xcompmgr...  Not sure if this means anything at all, but just saying I do not have issues of lag or cpu/ram usage with xcompmgr[/quote]

---

### Post by Jan-A6VMX on 2012-11-04
Thanks Toz!

Ubuntu 12.04 / LXDE / Openbox Window Manager / with xcompmgr running.

"own_window_argb_visual yes" made my own background visible behind conky, instead of the (well known, default orange-ish) ubuntu login background. 

All my "own-window" entries in ~/.conkyrc were:

```
own_window yes
own_window_class Conky
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_argb_visual yes
```

---

