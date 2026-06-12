---
title: "Conky Starts in GNOME, but not in LXDE"
date: 2012-02-10
forum: Desktop Environments
---

### Post by Viman on 2012-02-10
Hello all,

I'm running Ubuntu 11.10 (originally with Unity, but I installed LXDE on top), and used to be able to run Conky without trouble in whichever DE I wanted to.

As I was unable to use dual Monitors with LXDE, the past month had me using GNOME a lot more often, until I found an hour ago a way of setting it up in LXDE. To my surprise, Conky stubbornly refuses to run in LXDE, single or dual monitors alike. I have no idea why.

These are the messages that it prints as I invoke it from terminal:

```
:~$ conky
Conky: desktop window (1e0012f) is subwindow of root window (c7)
Conky: window type - override
Conky: drawing to created window (0x5000001)
Conky: drawing to double buffer

FATAL_ERROR: The server is not running!


FATAL_ERROR: The server is not running!


FATAL_ERROR: The server is not running!
(Note: from here and on it just keeps looping this line)
```

Anyone got a clue of what I could do?

I've searched just about the whole internet for some reproduction of this issue, and haven't seen anything close. If someone knows a thread explaining this issue, please let me know.

I will, too, post my .conkyrc upon request, though I don't think it has to do with the issue.

Thanks in advance.

---

### Post by Version Dependency on 2012-02-10
I have noticed in the past sometimes a conkyrc works fine in one DE and not so fine in another.  Post your .conkyrc and I will see if I get the same problem.

---

### Post by Viman on 2012-02-10
> **Version Dependency said:**
> I have noticed in the past sometimes a conkyrc works fine in one DE and not so fine in another.  Post your .conkyrc and I will see if I get the same problem.

Some news to me. Didn't (use to) happen to me before, as both LXDE and GNOME were fine and dandy with conky (a month ago). Anyway:

```
alignment top_right
background no
double_buffer yes
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
xftfont Ubuntu:size=12
gap_x 0
gap_y 26
minimum_size 300
maximum_width 300
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no

TEXT

${font Arial:bold:size=18}${alignc}All Systems are a Go!${font}
${hr 3}
${font Arial:size=30}${alignc}${time %H:%M:%S}${font}
${font Ubuntu:size=10}${alignc}You on time, bro?
${hr 3}
${font Arial:size=15}${alignc}STATUS:${font}
CPU1: ${cpu cpu1}% ${cpubar cpu1 10}
CPU2: ${cpu cpu2}% ${cpubar cpu2 10}
RAM: ${mem}/${memmax} ${membar 10}
SWAP: $swap
LINUX: ${fs_used}/${fs_size} ${fs_bar 10 /}
TEMP: ${acpitemp}°C
${hr 3}
${font Arial:size=15}${alignc}CONNECTIVITY:${font}
${alignc}Wi-Fi: 
UP:${upspeed wlan0}  DOWN:${downspeed wlan0}
Strength: ${wireless_link_bar 10 wlan0}
${alignc}LAN:
UP:${upspeed eth0}  DOWN:${downspeed eth0}
${hr 3}
${font Arial:size=15}${alignc}I'VE GOT THAT TUNE:${font}
${alignc}---
${if_running audacious2}${alignc}AUDACIOUS:
${alignc}${exec audtool2 current-song-tuple-data artist}
${alignc}${exec audtool2 --current-song}
${alignc}${exec audtool2 --current-song-output-length} - ${exec audtool2 --current-song-length}
${endif}
${if_running mocp}${alignc}MOC:
${alignc}${moc_artist}
${alignc}${moc_song}
${alignc}${moc_curtime} - ${moc_totaltime}
$endif

```

---

### Post by Rodney9 on 2012-02-10
I use these Window settings In Lubuntu using LXDE


```
# Window Settings
own_window yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```


Rodney

---

### Post by Viman on 2012-02-10
Hey, Rodney, that actually worked!
Conky is still spewing that "Fatal Error" message, but the window is full rendered and live again. Thank you!

---

### Post by Jan-A6VMX on 2013-01-05
got success with conky transparency in LXDE on debian squeezy, with pcmanfm running.
  In the conky config file (i.e. .conkyrc) I removed all 'own_window' lines, except the following:
  ```
own_window yes 
own_window_class conky 
own_window_transparent yes 
own_window_hints undecorated,below,skip_taskbar,sticky,skip_pager 
``` Adding again some often used lines like ```
own_window_argb_visual yes
```caused transparency to fail, or conky wouldn't start at all. Very strange...

---

