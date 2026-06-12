---
title: "Conky Crashes with Desktop"
date: 2010-01-08
forum: Desktop Environments
---

### Post by mathfreak123 on 2010-01-08
Hi, all! I have conky on my desktop, and it works most of the time. The only times I've noticed problems are when I do large file transfers from my computer to an external HD.

What happens during large file transfers is that Conky crashes, and then I realize that my desktop is also "dead" (as in, I can't highlight anything. The icon for my external HD is gone, even though it is still mounted and accessible. Right-clicking doesn't do anything either.). I tried Ctrl+Alt+Backspace, but that didn't work either. I can log out and back in to get everything working again, but that's a bit of a pain.

Anyone have any ideas? If you do, what information do you need?

I'm using the GNOME desktop on Ubuntu 9.10.

---

### Post by //ro0t on 2010-01-08
what conky config are you using ? :) i hade this problem an solve it with my config :)

it`s my config : 

    background yes
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
    ro0t - $sysname

    Uptime $alignr $uptime
    Load $alignr $loadavg

    Hostname $alignr $nodename
    wlan0 $alignr ${addr wlan0}

    

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
CPU: ${alignr}${freq} MHz
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

CPU1 ${alignr}${cpu cpu1}%
${cpubar 4 cpu1}
CPU2 ${alignr}${cpu cpu2}%
${cpubar 4 cpu2}

Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}
swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

${color white}NETWORK ${hr 1}${color}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107} ${alignr}${upspeedgraph eth0 25,107}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

---

### Post by mathfreak123 on 2010-01-08
Here is my conky file.

```
update_interval 1.0
use_xft yes
xftfont Bitstream Vera Sans:size=8
maximum_width 270

#color stuff
default_color white
color0 lightgrey
default_outline_color black
default_shade_color black

#text decoration
draw_shades yes

alignment bottom_right
uppercase no

#window stuff
double_buffer yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,sticky,below,skip_taskbar,skip_pager

#deals with graph stuff
show_graph_range yes
show_graph_scale yes

TEXT

Uptime:${color0} $uptime
${color}CPU1:${color0} ${freq 1} ${color}Mhz $alignr Usage:${color0} ${cpu cpu1}%
${cpugraph cpu1 0000ff ff0000 -t}
\
${color}CPU2:${color0} ${freq 2} ${color}Mhz $alignr Usage:${color0} ${cpu cpu2}%
${cpugraph cpu2 0000ff ff0000 -t}
\
${color}RAM usage:${color0} $mem/$memmax $alignr ${color0} $memperc% ${color}used
${membar}

Disk stats of /:$color ${fs_used /} / ${fs_size /} used $alignr ${color0} ${fs_used_perc /}% ${color}used
${fs_bar /}

Swap usage:${color0}$swap/$swapmax $color-${color0} $swapperc%
$color$swapbar

Wireless ESSID: ${color0}${wireless_essid wlan0} ${color}Bitrate: ${color0}${wireless_bitrate wlan0}

${color}Download:${color0} $alignr ${downspeedf wlan0} ${color}kB/s
${downspeedgraph wlan0 00ff00 ff0000 -t}

${color}Upload:${color0} $alignr ${upspeedf wlan0} ${color}kB/s
${upspeedgraph wlan0 00ff00 ff0000 -t}
```

---

### Post by //ro0t on 2010-01-08
use my config :)

---

### Post by mathfreak123 on 2010-01-08
I tried your config while doing a file transfer from my external. The desktop and conky didn't crash. I was thinking that maybe it was the "total_run_times" variable that prevented crashing, but I'm not sure if that's what it really is. Relative input is appreciated. :D

---

### Post by Spike-X on 2010-04-17
I had a problem with conky crashing every time I'd click on my desktop. Changing own_window_type from desktop to normal fixed this. Thanks!

---

### Post by Porter200el on 2010-09-30
> **Spike-X said:**
> I had a problem with conky crashing every time I'd click on my desktop. Changing own_window_type from desktop to normal fixed this. Thanks!

I logged into just to say thanks!  Great post, appreciate the help.

---

