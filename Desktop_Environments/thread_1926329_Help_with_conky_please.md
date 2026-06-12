---
title: "Help with conky please"
date: 2012-02-16
forum: Desktop Environments
---

### Post by Aleph_sev on 2012-02-16
[SOLVED]

Hi friends,

I need your help please.

I installed conky from synaptic, and did a .conkyrc file, but is not  working well. The fonts are not refreshing and The letters are overwritten on the previous.
And the background is selected yes but is black.

This is my conkyrc file, but with other the problem is the same.

(Sorry for my English)

```
[INDENT]background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 4.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 220
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color grey
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
TEXT
$sysname $kernel on $machine
Uptime $alignr $uptime
Load $alignr $loadavg
Hostname $alignr $nodename
wlan0 $alignr ${addr wlan0}
Inbound $alignr ${downspeed wlan0} kb/s
${downspeedgraph wlan0}
Outbound $alignr ${upspeed wlan0} kb/s
${upspeedgraph wlan0}
$processes processes ($running_processes running)
CPU $alignr ${cpu cpu0}%
${cpubar cpu0}
MEM $alignc $mem / $memmax $alignr $memperc%
$membar
/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}
/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}
swap $alignc $swap / $swapmax $alignr $swapperc%
${swapbar}
NAME $alignr PID    CPU
${top name 1} $alignr ${top pid 1} ${top cpu 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4}
${top name 5} $alignr ${top pid 5} ${top cpu 5}
${top name 6} $alignr ${top pid 6} ${top cpu 6}
${top name 7} $alignr ${top pid 7} ${top cpu 7}
${top name 8} $alignr ${top pid 8} ${top cpu 8}
[/INDENT]
```

---

### Post by Rodney9 on 2012-02-16
You should ask here - [http://ubuntuforums.org/showthread.php?t=281865&highlight=conky&page=1926](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky&page=1926)

You might find conky experts to help.

Rodney

---

### Post by Aleph_sev on 2012-02-16
Thanks Rodney9, I'll do.

---

### Post by Toz on 2012-02-16
This might help with the transparency issue with xfce: [http://blog.mmassonnet.info/2011/08/xfce-48-with-conky.html]("http://blog.mmassonnet.info/2011/08/xfce-48-with-conky.html")

---

### Post by Aleph_sev on 2012-02-16
Thanks Toz,

now the transparency and overwriting are solved, but a new problem came: 

a rectangular symbol appear now at the end of the lines...

Any idea?

```
background yes
use_xft yes
xftfont Sans:size=8
xftalpha 1
update_interval 1.0
total_run_times 0
own_window yes
own_window_class Conky
own_window_type desktop
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_argb_visual yes
own_window_argb_value 100
double_buffer yes
minimum_size 200 200
maximum_width 200
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color white
alignment top_right
gap_x 12
gap_y 60
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
${font sans-serif:bold:size=8}PORTATIL ${hr 2}
${font sans-serif:normal:size=8}$sysname $kernel $alignr $machine
Host:$alignr$nodename
Tiempo encendido:$alignr$uptime
File System: $alignr${fs_type}

${font sans-serif:bold:size=8}PROCESADORES ${hr 2}
${font sans-serif:normal:size=8}${cpugraph cpu1}
CPU1: ${cpu cpu1}% ${cpubar cpu1}

${font sans-serif:bold:size=8}MEMORIA ${hr 2}
${font sans-serif:normal:size=8}RAM $alignc $mem / $memmax $alignr $memperc%
$membar

${font sans-serif:bold:size=8}DISCOS ${hr 2}
${font sans-serif:normal:size=8}/ $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_used_perc /}%
${fs_bar /}
SWAP $alignc ${swap} / ${swapmax} $alignr ${swapperc}%
${swapbar}

${font sans-serif:bold:size=8}PROCESOS ${hr 2}
${font sans-serif:normal:size=8}${top_mem name 1}${alignr}${top mem 1} %
${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %

${font sans-serif:bold:size=8}INTERNET ${hr 2}
${font sans-serif:normal:size=8}IP address: $alignr ${addr ath0}
ESSID: $alignr ${wireless_essid ath0}
Connection quality: $alignr ${wireless_link_qual_perc ath0}%
${downspeedgraph ath0}
DLS:${downspeed ath0} kb/s $alignr total: ${totaldown ath0}
${upspeedgraph ath0}
ULS:${upspeed ath0} kb/s $alignr total: ${totalup ath0}

http://${color grey}$alignc${execi 3600 xfce4-about --version | head -1 | sed 's/xfce4-about/Xfce/'}
```[IMG]https://lh3.googleusercontent.com/-8XydGR1vACQ/Tz0cvWOk3SI/AAAAAAAAOZw/Rp-ji0ztB2Y/s800/Captura%2520de%2520pantalla%2520-%2520160212%2520-%252016%253A10%253A05.png[/IMG]

---

### Post by Toz on 2012-02-16
I just ran your script and it works fine here. What program are you using to edit/save the conky script file? Looks like there is some sort of code (line feed or carriage return) at the end of every line.

---

### Post by Aleph_sev on 2012-02-16
Hi Toz,

I use Leafpad.

---

### Post by Toz on 2012-02-16
Try fiddling with the **override_utf8_locale** and **use_xft** settings in the following combinations:
```

use_xft yes
override_utf8_locale yes

```
```

use_xft no
override_utf8_locale yes

```
```

use_xft no
override_utf8_locale no

```

---

### Post by Aleph_sev on 2012-02-17
Hi Toz,

the problem is Solved.

This was the solution.

> Could be your config is saved with Windows line endings.
Open your config in gedit and choose File > Save As
and make sure the line ending is Unix/Linux.                      Thanks.

---

