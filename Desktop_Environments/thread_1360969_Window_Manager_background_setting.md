---
title: "Window Manager background setting"
date: 2009-12-21
forum: Desktop Environments
---

### Post by whiterabbit7500 on 2009-12-21
I recently reformatted my PC to Kubuntu 9.1, and love it so far. I'm currently configuring my Conky file, and I'm running into a bit of a problem with making it transparent. The .conf file is below.

```
# .conkyrc

     double_buffer yes
    update_interval 3.0
    background yes

    own_window yes
    own_window_transparent yes
    own_window_type normal
    own_window_hints undecorated,below,skip_taskbar

    use_xft yes
    override_utf8_locale no
    xftfont Bitstream Vera Sans Mono:size=7
    xftalpha 0.8
    draw_shades no
    draw_outline no
    draw_borders no
    uppercase yes
    use_spacer no

    border_margin 9
    border_width 0

    default_color light grey
    default_shade_color black
    default_outline_color black

    alignment top_right
    minimum_size 200
    gap_x 9
    gap_y 9

    TEXT
    ${alignc}${time %I:%M %p}, ${time %a}., ${time %b. %e}, ${time %G}
    ${alignc}Ubuntu Linux $kernel
    ${alignc}hostname $nodename at ${addr eth0}
    ${alignc}${execi 1000 cat /proc/cpuinfo | grep ‘model name’ | sed -e
    ’s/model name.*: //’}
    ${alignc}$uptime uptime

    CPU Load: ${alignr}$cpu%
    ${cpugraph 20,200 000000 ffffff}
    Load averages: ${alignr}$loadavg

    Processes: ${alignr}$running_processes of $processes running
    Highest CPU usage:
    ${color yellow} ${top name 1}${alignr}${top cpu 1}
    ${color}${top name 2}${alignr}${top cpu 2}
    ${top name 3}${alignr}${top cpu 3}
    ${top name 4}${alignr}${top cpu 4}
    Highest memory usage:
    ${color yellow} ${top_mem name 1}${alignr}${top_mem mem 1}
    ${color}${top_mem name 2}${alignr}${top_mem mem 2}
    ${top_mem name 3}${alignr}${top_mem mem 3}
    ${top_mem name 4}${alignr}${top_mem mem 4}

    Resources:
    Memory usage: ${alignr}${memperc}% (${mem}b/${memmax}b)
    ${membar 3,200}
    Swap usage: ${alignr}${swapperc}% (${swap}b/${swapmax}b)
    ${swapbar 3,200}
    HDD free: ${alignr}${fs_free_perc /}% (${fs_free /}b/${fs_size /}b)
    ${fs_bar 3,200 /}

    NET:
    Up:${alignr}${upspeed eth0}Kbps, ${totalup eth0}b total
    ${upspeedgraph eth0 20,200 000000 ffffff}
    Down: ${alignr}${downspeed eth0}Kbps, ${totaldown eth0}b total
    ${downspeedgraph eth0 20,200 000000 ffffff}
```

If I'm reading correctly, the above code should make it transparent, but It still has a black background. I'm reading in the [Conky FAQ]("http://conky.sourceforge.net/faq.html") that it might be due to the Window Manager seating the image on a separate layer. I'm trying to use some of the tools described in question 6 on that page, but nothing seems to be installing, or working correctly. any help?

---

