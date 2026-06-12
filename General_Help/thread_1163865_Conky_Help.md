---
title: "Conky Help"
date: 2009-05-19
forum: General Help
---

### Post by Orlsend on 2009-05-19
Hi Been trying out conky and it cool! though I would like to make some changes to it. 

First its the border of conky:

I really don't want one, like I have shown in the attachment.

And second it is when I first boot up conky is there but a soon as I click on the desktop it hides although it is still running, but you cann it again once you initiate the shut down.

I am on Jaunty 9,04 with compiz.

 and here is my Conky file:

```
background yes
font Snap.se:size=8
xftfont Snap.se:size=8
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type desktop
own_window_transparent yes
own_window_hints below
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 206 5
maximum_width 206
default_color ffffff
default_shade_color 000000
default_outline_color 000000
alignment top_right
gap_x 6
gap_y 8
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

CPU ${alignc} ${freq}MHz / ${acpitemp}C ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph cccccc ffffff}

RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}

SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${hr 1}
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${hr 1}
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${font Aerial:style=Bold:pixelsize=12}FILESYSTEM ${font Snap.se:size=8}${hr 1}

Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /home}

${font Aerial:style=Bold:pixelsize=12}NETWORK ${font Snap.se:size=8}${hr 1}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107 cccccc ffffff} ${alignr}${upspeedgraph eth0 25,107 cccccc ffffff}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

```

---

### Post by iiska on 2009-05-19
You should get rid of the border by setting own_window_type to override instead of desktop.

Edit: Changing the own_window_type actually fixes both your problems. ;)

---

### Post by VCoolio on 2009-05-19
the 'borders' are dropshadows that probably are drawn by compiz. In the compiz settings manager > window decoration plugin find the entry for window shadows and fill in
```
any  & !(class=conky)
```
Don't know if override takes care of that, at least this will.

---

### Post by Orlsend on 2009-05-20
Yeah but them its just sticking-out, so its on the way of most of my apps! any ideas?

---

### Post by iiska on 2009-05-20
> **Orlsend said:**
> Yeah but them its just sticking-out, so its on the way of most of my apps! any ideas?

Have you already tried changing the own_window_type to override in the .conkyrc. That worked for me.

---

### Post by Orlsend on 2009-05-20
Yeah that what does. for sure it will fix my problem but yet will make my experience poor since the conky will on top of all the windows.

I will like it to sat in the desktop, but not on top of my windows.

---

### Post by iiska on 2009-05-20
> **Orlsend said:**
> Yeah that what does. for sure it will fix my problem but yet will make my experience poor since the conky will on top of all the windows.

I will like it to sat in the desktop, but not on top of my windows.

Option "own_window_hints below" should put it below other windows, but looks like you have already included that one.

---

### Post by Orlsend on 2009-05-20
As you can see in my conky file that line is already present.

---

