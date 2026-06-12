---
title: "conky problems. please help."
date: 2007-07-12
forum: Desktop Effects &amp; Customization
---

### Post by pjones0404 on 2007-07-12
i just installed conky on my new fiesty install. the issue that i have is that it only appears on one desktop. it also shows on my workplace switcher. how can i fix this? i had it on a edgy machine and it worked fine.

here is a copy of my .conkyrc file.

own_window yes
own_window_hints undecorated,below,skip_taskbar
background no
double_buffer yes
use_spacer yes
use_xft yes
update_interval 2.0
minimum_size 200 5
maximum_width 270
draw_shades yes
draw_outline no 
draw_borders no
draw_graph_borders no
uppercase no # set to yes if you want all text to be in uppercase
border_margin 4
border_width 1
default_color white
default_shade_color black
default_outline_color white
own_window_transparent yes
alignment top_right
gap_x 10
gap_y 10
override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8


TEXT
${color }${time %a, %e %B %G}${alignr}${time %T %Z} / ${tztime UTC %T} UTC
${color lightgrey}System uptime: ${color #ddaa00}${uptime}  

${color }Ubuntu 7.04 Feisty Fawn${alignr}${kernel} ${machine}

${color slate grey}Processor: ${color }AMD AthlonXP 3200  
${color lightgrey}${tab 20}Freqency: ${color }${freq_g cpu0}Ghz
${color lightgrey}${tab 20}Temperature: ${color }${acpitemp}C   (${acpitempf}F)
${color lightgrey}${tab 20}Load: ${color #ddaa00}${cpu}%${alignr }${color }${cpubar 6,180}	
${color lightgrey}${tab 20}CPU History ${color }${tab 45}${cpugraph cpu0 10,180 000000 ffffff}
${color lightgrey}${tab 20}Processes Running: ${color }${running_processes}
${color lightgrey}${tab 20}Processes Sleeping: ${color }${processes}
	
${color lightgrey}${tab 20}Top CPU Processes: $alignr CPU%
${color #ddaa00}${tab 40}${top name 1}$alignr${top cpu 1}
${color }${tab 40}${top name 2}$alignr${top cpu 2}
${color }${tab 40}${top name 3}$alignr${top cpu 3}

${color slate grey}Memory: 
${color }${tab 20}${memmax} available / ${mem} in use
${color lightgrey}${tab 20}Used: ${color #ddaa00}${memperc}%${alignr}${color }${membar 6,180}

${color lightgrey}${tab 20}Top Memory Processes: $alignr MEM%
${color #ddaa00}${tab 40}${top_mem name 1}$alignr${top_mem mem 1}
${color }${tab 40}${top_mem name 2}$alignr${top_mem mem 2}
${color }${tab 40}${top_mem name 3}$alignr${top_mem mem 3}

${color slate grey}Disk: /dev/hda3 Linux (ext3)
${color lightgrey}${tab 20}Total: ${color }${fs_size} 
${color lightgrey}${tab 20}Used: ${color }${fs_used}
${color lightgrey}${tab 20}Available: ${color }${fs_free}
${color lightgrey}${tab 20}Free: ${color #ddaa00}${fs_free_perc}%${color }${alignr}${fs_bar 6,180}
${color lightgrey}${tab 20}I/O History: ${tab 45}${diskiograph 10,180 000000 ffffff}

${color slate grey}Network:
${color lightgrey}${tab 20}IP: ${color }${addr eth0}
${color lightgrey}${tab 20}DL ${color #ddaa00}${downspeedf eth0}kb/s${tab 45}${downspeedgraph eth0 10,180 000000 ffffff}
${color lightgrey}${tab 20}UL ${color #ddaa00}${upspeedf eth0}kb/s${tab 45}${upspeedgraph eth0 10,180 000000 ffffff}

${color lightgrey}${tab 20}Connections  ${alignr} Service/Port ${color }
${tab 20}${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tab 20}${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tab 20}${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tab 20}${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tab 20}${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tab 20}${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}


thanks in advance

---

### Post by Alex&amp;Linux on 2007-07-12
Youve got it running in its own window correct?
That means that its a window like any other app may display.
It'll only be on the desktop you leave it on!

If you want it drawn on all desktops, simply use the argument -a [top,bottom]_[left,right]
 for example

  ```
$ conky -a top_right
```

That will glue it in place.

Heres the help file:
```
ajn@ajn-desktop:~$ conky -help
Usage: conky [OPTION]...
Conky is a system monitor that renders text on desktop or to own transparent
window. Command line options will override configurations defined in config
file.
   -V            version
   -c FILE       config file to load instead of $HOME/.conkyrc
   -d            daemonize, fork to background
   -h            help
   -a ALIGNMENT  text alignment on screen, {top,bottom}_{left,right}
   -f FONT       font to use
   -o            create own window to draw
   -b            double buffer (prevents flickering)
   -w WIN_ID     window id to draw
   -x X          x position
   -y Y          y position
   -t TEXT       text to render, remember single quotes, like -t '$uptime'
   -u SECS       update interval
   -i NUM        number of times to update Conky
ajn@ajn-desktop:~$ 

```

---

