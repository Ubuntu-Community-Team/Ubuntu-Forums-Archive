---
title: "Conky Icon problems"
date: 2007-09-03
forum: Desktop Effects &amp; Customization
---

### Post by rstuart on 2007-09-03
Hi Guys,

I am running conky on my laptop and always loose my icons when i do. I have seen what they suggest on the conky site and while the double buffer stops the flickering, it doesn't save my icons from certain death. I really dislike the idea of using the own_window option. I prefer it to be on the desktop.

My .conkyrc is below, any suggestions?

```

# conky configuration
# edited by ryan+conky@stuart.id.au 

background no
use_xft yes
xftfont Terminus:size=8
out_to_console no
update_interval 2.0
total_run_times 0
own_window no
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
stippled_borders 8
border_margin 4
border_width 1
default_color white
default_shade_color black
default_outline_color white
alignment top_right
gap_y 1
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
use_spacer yes

TEXT

${color slate grey}${time %a, } ${color }${time %e %B %G}
${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${color slate grey}UpTime: ${color }$uptime
${color slate grey}BATTERY: ${color }$battery
${color slate grey}CPU:${color } $cpu%  ${acpitemp}C
${cpugraph 20,130 ddaa00 ddaa00}
${color slate grey}Load: ${color }$loadavg
${color slate grey}Processes: ${color }$processes  
${color slate grey}Running:   ${color }$running_processes

${color slate grey}Highest CPU:
${color #ddaa00} ${top name 1}$alignr${top_mem cpu 1}
${color lightgrey} ${top name 2}$alignr${top cpu 2}
${color lightgrey} ${top name 3}$alignr${top cpu 3}
${color lightgrey} ${top name 4}$alignr${top cpu 4}

${color slate grey}Highest MEM:
${color #ddaa00} ${top_mem name 1}$alignr${top_mem mem 1}
${color lightgrey} ${top_mem name 2}$alignr${top_mem mem 2}
${color lightgrey} ${top_mem name 3}$alignr${top_mem mem 3}
${color lightgrey} ${top_mem name 4}$alignr${top_mem mem 4}

${color slate grey}MEM: ${color }$memperc% $mem/$memmax
${membar 3,100}
${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${swapbar 3,100}

${color slate grey}DISK: ${color }$diskio
${diskiograph 20,130 ddaa00 ddaa00}

${color slate grey}WIRELESS: ${color }${linkstatus eth1}%
${color}Up: ${color }${upspeed eth1} k/s
${upspeedgraph eth0 20,130 ddaa00 ddaa00}
${color}Down: ${color }${downspeed eth1}k/s${color}
${downspeedgraph eth1 20,130 ddaa00 ddaa00}

```

Thanks

---

### Post by happy-and-lost on 2007-09-03
Same problem here :(

---

### Post by psyopper on 2007-09-03
Take a look at [http://conky.sourceforge.net]("http://conky.sourceforge.net"). I think your problem has to do with setting you maximum size, for instance:
```

minimum_size 200 5
maximum_width 270

```

Otherwise your conky window may come out maximized, and even though you have made it "clear" it still overlays the icons. The clear background in Conky is a trick, like the clear background in a Terminal window. It actually takes a snapshot of the desktop background and reporduces it as the background of your Conky window.

I also noticed your placement is upper right. Do you have icons in the upper right that may be covered by the Conky window placement? [Take a look at this thread]("http://ubuntuforums.org/showthread.php?t=281865") for a LOT of tips and tricks for Conky.

---

### Post by rstuart on 2007-09-04
fixed thanks

```

# conky configuration
# edited by ryan+conky@stuart.id.au 

background no
use_xft yes
xftfont Terminus:size=8
out_to_console no
update_interval 2.0
total_run_times 0
own_window no
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
stippled_borders 8
border_margin 4
border_width 1
default_color white
default_shade_color black
default_outline_color white
alignment top_right
maximum_width 270
# Following lines fixed icon problem
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
######################
gap_y 1
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
use_spacer yes

TEXT

${color slate grey}${time %a, } ${color }${time %e %B %G}
${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${color slate grey}UpTime: ${color }$uptime
${color slate grey}BATTERY: ${color }$battery
${color slate grey}CPU:${color } $cpu%  ${acpitemp}C
${cpugraph 20,130 ddaa00 ddaa00}
${color slate grey}Load: ${color }$loadavg
${color slate grey}Processes: ${color }$processes  
${color slate grey}Running:   ${color }$running_processes

${color slate grey}Highest CPU:
${color #ddaa00} ${top name 1}$alignr${top cpu 1}%
${color lightgrey} ${top name 2}$alignr${top cpu 2}%
${color lightgrey} ${top name 3}$alignr${top cpu 3}%
${color lightgrey} ${top name 4}$alignr${top cpu 4}%

${color slate grey}Highest MEM:
${color #ddaa00} ${top_mem name 1}$alignr${top_mem mem 1}%
${color lightgrey} ${top_mem name 2}$alignr${top_mem mem 2}%
${color lightgrey} ${top_mem name 3}$alignr${top_mem mem 3}%
${color lightgrey} ${top_mem name 4}$alignr${top_mem mem 4}%

${color slate grey}MEM: ${color }$memperc% $mem/$memmax
${membar 3,100}
${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${swapbar 3,100}

${color slate grey}DISK: ${color }$diskio
${diskiograph 20,130 ddaa00 ddaa00}

${color slate grey}WIRELESS: ${color }${linkstatus eth1}%
${color}Up: ${color }${upspeed eth1} k/s
${upspeedgraph eth0 20,130 ddaa00 ddaa00}
${color}Down: ${color }${downspeed eth1}k/s${color}
${downspeedgraph eth1 20,130 ddaa00 ddaa00}

```

---

