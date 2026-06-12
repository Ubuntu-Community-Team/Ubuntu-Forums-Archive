---
title: "Emerald Window Decorator + Conky"
date: 2009-01-17
forum: General Help
---

### Post by ProgenitorVirus on 2009-01-17
I'm using Emerald window manager, which adds a glow to the sides of windows.  I have Conky up (I stole it from that large thread as I didn't care to bother learning in depth how to code them), and edited it with my settings; so I know only a few basic things of it.

I'm using a transparent and borderless window, but there's still glow at the sides where the border would be.

Is there any way to remove this?  Here's my conkyrc

background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 280
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 24
gap_y 60
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
SYSTEM


     $sysname $kernel on $machine

     Uptime $alignr $uptime
     Load $alignr $loadavg


NETWORK


      Hostname $alignr $nodename
      eth1 $alignr ${addr eth1}

      Inbound $alignr ${downspeed eth1} kb/s
      ${downspeedgraph eth1}
      Outbound $alignr ${upspeed eth1} kb/s
      ${upspeedgraph eth1}


PROCESSES


      $processes Processes ($running_processes running)

      Top Processes

            CPU $alignr CPU% MEM%

            ${top name 1}$alignr${top cpu 1}${top mem 1}
            ${top name 2}$alignr${top cpu 2}${top mem 2}
            ${top name 3}$alignr${top cpu 2}${top mem 3}

            MEM $alignr CPU% MEM%

            ${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
            ${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
            ${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}


USAGE


      CPU $alignr ${cpu cpu0}%
      ${cpubar cpu0}

      MEM $alignc $mem / $memmax $alignr $memperc%
      $membar

      swap $alignc $swap / $swapmax $alignr $swapperc%
      ${swapbar}

      / $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_used_perc /}%
      ${fs_bar /}

      /media/files $alignc ${fs_used /media/files} / ${fs_size /media/files} $alignr ${fs_used_perc /media/files}%
      ${fs_bar /media/files}

---

### Post by Wartender on 2009-01-17
in window decorations in compizconfig settings manager, in the shadow window box, type in
!title=Conky

---

### Post by tomski on 2011-04-17
thnx helped me too

---

