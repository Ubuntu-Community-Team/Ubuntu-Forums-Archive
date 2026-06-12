---
title: "Conky making X take up 30% cpu constantly."
date: 2010-10-11
forum: Desktop Environments
---

### Post by xyexz on 2010-10-11
Just curious if anyone else is using Conky and if so is it making their X take 25-30% cpu constantly?

I'm running a core i7 1.6GHz cpu & gt 300m gpu you'd think it wouldn't put that much load on anything.

I can post my config should anyone want to investigate, I know for sure it's Conky because as soon as I killall conky X takes only around 3% cpu.

I am using Compiz and I just upgraded to 10.10 although I can't recall if the same issue occured in 10.04.

---

### Post by Alessandro.g89 on 2010-10-11
yes, post your config

---

### Post by xyexz on 2010-10-11
Ok here is my config:

[PHP]# Locale, fonts and font sizes.
use_xft yes
xftfont Droid Sans:size=9
override_utf8_locale yes

# Conky performance
update_interval 1
total_run_times 0
double_buffer yes
#no_buffers yes
net_avg_samples 2
text_buffer_size 1044

# Execute it in its own window
background no
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Borders, margins.
draw_borders no
# border_margin 1

# Own window color
own_window_colour 393834

# Font colors
default_color B7B2AD
#default_color EFEEED

# Text shadows
draw_shades no

# Header colors
color0 DD3A21

# Minimum dimensions
minimum_size 1920 200

default_bar_size 100 10

# Conky positioning.
alignment bottom_left
gap_x 0
gap_y 0

# Output
TEXT
${image ~/.conkytheme/pix/frame_1920_200.png -p 0,0 1920x200}
${voffset 25}${font Droid Sans:style=Bold:size=12}${color0}${goto 256}CPUs @ ${freq}MHz${goto 470}Disks${goto 708}Network @ ${wireless_essid wlan0} ${wireless_link_qual_perc wlan0}%${goto 1000}Temperatures${goto 1190}Time & Date${font}${color}
${voffset 10}${goto 256}CPU1: ${goto 300}${cpubar cpu1 10,100}${font Droid Sans:style=Bold:size=9}  ${cpu cpu1}%${font}${goto 470}System (/):${goto 574}${fs_used /} / ${fs_size /}${goto 708}Up Speed: ${goto 808}${upspeedgraph wlan0 10,100 B7B2AD B7B2AD}${font Droid Sans:style=Bold:size=9}  ${upspeed wlan0}${font}${goto 1000}CPU: ${goto 1040}${execi 4 sensors -f | grep -A 0 'temp2' | cut -c14-18} ºF${goto 1190}${time %H:%M}  ${time %d/%m/%Y}
${goto 15}Kernel: ${goto 85}${kernel}${goto 256}CPU2: ${goto 300}${cpubar cpu2 10,100}${font Droid Sans:style=Bold:size=9}  ${cpu cpu2}%${font}${goto 574}${fs_bar 10,100 /}${goto 708}Down Speed: ${goto 808}${downspeedgraph wlan0 10,100 B7B2AD B7B2AD}${font Droid Sans:style=Bold:size=9}  ${downspeed wlan0}${font}${goto 1000}GPU: ${goto 1040}${execi 4 echo $((((`nvidia-settings -q gpucoretemp | grep ':0.0' | cut -c 47-48`+40)*9/5)-40))} ºF${goto 1190}${time %A}, ${time %d} ${time %B} ${time %Y}
${goto 15}RAM: ${goto 85}${membar 10,100}${font Droid Sans:style=Bold:size=9}  $memperc%${font}${goto 256}CPU3: ${goto 300}${cpubar cpu3 10,100}${font Droid Sans:style=Bold:size=9}  ${cpu cpu3}%${font}${goto 470}Home (/Home):${goto 574}${fs_free /home} / ${fs_size /home}${goto 708}Uploaded: ${goto 808}${totalup wlan0}
${goto 15}SWAP: ${goto 85}${swapbar 10,100}${font Droid Sans:style=Bold:size=9}  $swapperc%${font}${goto 256}CPU4: ${goto 300}${cpubar cpu4 10,100}${font Droid Sans:style=Bold:size=9}  ${cpu cpu4}%${font}${goto 574}${fs_bar 10,100 /home}${goto 708}Downloaded: ${goto 808}${totaldown wlan0}
${goto 15}Battery: ${goto 85}${battery_bar}${font Droid Sans:style=Bold:size=9}  ${battery_percent}%${font}${goto 256}CPU5: ${goto 300}${cpubar cpu5 10,100}${font Droid Sans:style=Bold:size=9}  ${cpu cpu5}%${font}${goto 708}Public IP: ${goto 808}${execi 10800 ~/Scripts/find_public_ip.py}
${goto 85}${font Droid Sans:style=Bold:size=9}${acpiacadapter} - ${battery_time}${font}${goto 256}CPU6: ${goto 300}${cpubar cpu6 10,100}${font Droid Sans:style=Bold:size=9}  ${cpu cpu6}%${font}${goto 708}Local IP: ${goto 808}${addr wlan0}
${goto 256}CPU7: ${goto 300}${cpubar cpu7 10,100}${font Droid Sans:style=Bold:size=9}  ${cpu cpu7}%${font}
${goto 15}Uptime: ${goto 85}${uptime}${goto 256}CPU8: ${goto 300}${cpubar cpu8 10,100}${font Droid Sans:style=Bold:size=9}  ${cpu cpu8}%${font}${goto 470}High CPU: ${font Droid Sans:style=Bold:size=9}${execi 10 ps -eo pid,%cpu,cmd --no-heading | sort -r -nk2 | head -n 1 | cut -c1-40}...${font}[/PHP]

[IMG]http://dl.dropbox.com/u/10833963/Photos/ubuntu_desktop.png

---

### Post by xyexz on 2010-10-12
Bump

---

### Post by xyexz on 2010-10-13
bump

---

### Post by Alessandro.g89 on 2010-10-31
sorry for the late response. the cause of your problem could be in the "execi" stanzas, as each of them creates a new process and that happens every second. try not using them and see if cpu usage gets lower

---

