---
title: "Conky is flickering"
date: 2015-08-31
forum: Desktop Environments
---

### Post by ShadowCore on 2015-08-31
There is probably a very easy solution to this, but I haven't found it :(
My conky is flickering, and I can't figure out why. Below is my .conkyrc, do you experts need anything else?

```


[LIST=1]
[*][COLOR=#000000]# set to yes if you want Conky to be forked in the background[/COLOR]

[*][COLOR=#000000]background yes[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# Create own window instead of using desktop (required in nautilus)[/COLOR]

[*][COLOR=#000000]own_window yes[/COLOR]

[*][COLOR=#000000]own_window_type override[/COLOR]

[*][COLOR=#000000]own_window_transparent yes[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# Use Xft?[/COLOR]

[*][COLOR=#000000]use_xft yes[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# Set conky on the bottom of all other applications[/COLOR]

[*][COLOR=#000000]on_bottom yes[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# Update interval in seconds[/COLOR]

[*][COLOR=#000000]update_interval 2[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# This is the number of times Conky will update before quitting.[/COLOR]

[*][COLOR=#000000]# Set to zero to run forever.[/COLOR]

[*][COLOR=#000000]total_run_times 0[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# Use double buffering (reduces flicker, may not work for everyone)[/COLOR]

[*][COLOR=#000000]double_buffer yes[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# Default colors and also border colors[/COLOR]

[*][COLOR=#000000]default_color white[/COLOR]

[*][COLOR=#000000]default_shade_color black[/COLOR]

[*][COLOR=#000000]default_outline_color black[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# Text alignment, other possible values are commented[/COLOR]

[*][COLOR=#000000]#alignment top_left[/COLOR]

[*][COLOR=#000000]alignment top_right[/COLOR]

[*][COLOR=#000000]#alignment bottom_left[/COLOR]

[*][COLOR=#000000]#alignment bottom_right[/COLOR]

[*][COLOR=#000000]#alignment none[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# Gap between borders of screen and text[/COLOR]

[*][COLOR=#000000]# same thing as passing -x at command line[/COLOR]

[*][COLOR=#000000]gap_x 12[/COLOR]

[*][COLOR=#000000]gap_y 40[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# Subtract file system buffers from used memory?[/COLOR]

[*][COLOR=#000000]no_buffers yes[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# set to yes if you want all text to be in uppercase[/COLOR]

[*][COLOR=#000000]uppercase no[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# number of cpu samples to average[/COLOR]

[*][COLOR=#000000]# set to 1 to disable averaging[/COLOR]

[*][COLOR=#000000]cpu_avg_samples 2[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# number of net samples to average[/COLOR]

[*][COLOR=#000000]# set to 1 to disable averaging[/COLOR]

[*][COLOR=#000000]net_avg_samples 2[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# Force UTF8? note that UTF8 support required XFT[/COLOR]

[*][COLOR=#000000]override_utf8_locale yes[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# Add spaces to keep things from moving about?  This only affects certain objects.[/COLOR]

[*][COLOR=#000000]use_spacer none[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]# stuff after 'TEXT' will be formatted on screen[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]TEXT[/COLOR]

[*][COLOR=#000000]${color #F6F9F9}$NODENAME ${hr 2}$color ${alignr}[/COLOR]

[*][COLOR=#000000]${color #909090}Kernel: $color${alignr}${kernel}[/COLOR]

[*][COLOR=#000000]${color #909090}Load: $color${alignr}${loadavg}[/COLOR]

[*][COLOR=#000000]${color #909090}Date: $color${alignr}${time %a, %D}[/COLOR]

[*][COLOR=#000000]${color #909090}Time: $color${alignr}${time %I:%M %p}[/COLOR]

[*][COLOR=#000000]${color #909090}Uptime: $color${alignr}${uptime}[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]${color #F6F9F9}PROCESSING ${hr 2}$color[/COLOR]

[*][COLOR=#000000]${color #909090}CPU 0:$color     ${alignr}${cpu cpu0}%[/COLOR]

[*][COLOR=#000000]${color #909090}CPU 1:$color     ${alignr}${cpu cpu1}%[/COLOR]

[*][COLOR=#000000]${color #909090}${cpugraph 20,180 000000 448FC6}[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]${color #F6F9F9}DATA ${hr 2}$color[/COLOR]

[*][COLOR=#000000]${color #909090}RAM Usage: $color${mem} of $memmax$color[/COLOR]

[*][COLOR=#000000]$memperc% $membar[/COLOR]

[*][COLOR=#000000]${color #909090}Swap Usage: $color${swap} of $swapmax$color[/COLOR]

[*][COLOR=#000000]$swapperc% ${swapbar}[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]${color #909090}Processes: $color$processes  ${color #909090}Running: $color$running_processes[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]${color #F6F9F9}FILESYSTEM ${hr 2}$color[/COLOR]

[*][COLOR=#000000]${color #909090}Root:  $color${alignr}${fs_free_perc /}% Free$color  [/COLOR]

[*][COLOR=#000000]${fs_bar 6 /}$color[/COLOR]

[*][COLOR=#000000]${color #909090}Home:  $color${alignr}${fs_free_perc /home}% Free$color  [/COLOR]

[*][COLOR=#000000]${fs_bar 6 /home}$color[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]${color #F6F9F9}NETWORK ${hr 2}$color[/COLOR]

[*][COLOR=#000000]${color #909090}Wired IP: $color${addr eth0}[/COLOR]

[*][COLOR=#000000]${color #909090}Upload:$color     ${alignr}${upspeed eth0}kb/s${color #909090}[/COLOR]

[*][COLOR=#000000]${color #909090}Download:$color ${alignr}${downspeed eth0}kb/s${color #909090}[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]${color #909090}Download:${alignr} Upload:$color[/COLOR]

[*][COLOR=#000000]${downspeedgraph eth0 25,80 000000 4AC644} ${alignr}${upspeedgraph eth0 25,80 000000 44C69F}$color[/COLOR]

[*][COLOR=#000000]${color #909090}Down:$color ${totaldown eth0} ${alignr}${color #909090}Up:$color ${totalup eth0}[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]${color #F6F9F9}CALENDAR ${hr 2}$color[/COLOR]

[*][COLOR=#000000]${color #FFFFFF}${execi 300 ~/.calendar.sh}[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]${color #F6F9F9}Name             PID    CPU%[/COLOR]

[*][COLOR=#000000]${color #909090}${top name 1} ${top pid 1} ${top cpu 1}[/COLOR]

[*][COLOR=#000000]${color #909090}${top name 2} ${top pid 2} ${top cpu 2}[/COLOR]

[*][COLOR=#000000]${color #909090}${top name 3} ${top pid 3} ${top cpu 3}[/COLOR]

[*][COLOR=#000000]${color #909090}${top name 4} ${top pid 4} ${top cpu 4}[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]${color #F6F9F9}Name             PID    MEM%[/COLOR]

[*][COLOR=#000000]${color #909090}${top name 1} ${top pid 1} ${top mem 1}[/COLOR]

[*][COLOR=#000000]${color #909090}${top name 2} ${top pid 2} ${top mem 2}[/COLOR]

[*][COLOR=#000000]${color #909090}${top name 3} ${top pid 3} ${top mem 3}[/COLOR]

[*][COLOR=#000000]${color #909090}${top name 4} ${top pid 4} ${top mem 4}[/COLOR]
[/LIST]

```

---

### Post by QDR06VV9 on 2015-08-31
Sometimes this needs to added as well
```
double_buffer yes
```
See if that makes it happy if not post back your entire .conkyrc script.
Ok I could not scroll for a moment in your tags I see you have that already
This has worked for me also 
```
no_buffers yesoverride_utf8_locale yes


own_window yes
own_window_type normal
_**own_window_hints below,sticky,undecorated,skip_taskbar,skip_pager**_
# own_window_colour black
own_window_transparent yes


# ARGB can be used for real transparency,
# note that a composite manager is required for real transparency
own_window_argb_visual no
```

Regards

---

