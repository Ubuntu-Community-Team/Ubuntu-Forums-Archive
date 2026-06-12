---
title: "Conky is not working !!"
date: 2009-05-16
forum: Desktop Environments
---

### Post by Priyank .aka. Owen on 2009-05-16
[I][B]Hi, i am new to linux,

i want set up a conky 

i installed conky from terminal first with this "[/B][/I]***sudo apt-get install conky***[I][B]"

then created a folder named "CONKY" in home and in that folder i created a file name "conkyrc" with this code in it [/B][/I]> background no
xftfont Terminus:size=8
xftalpha 0.8
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 150 5
maximum_width 205
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no

TEXT
$stippled_hr
${color yellow}$nodename${color white} - Ubunut ($machine)
$stippled_hr
Kernel: $alignr $kernel
Uptime: $alignr $uptime
$stippled_hr
CPU1: ${cpu cpu1}% ${alignr} CPU2: ${alignr} ${cpu cpu2}%
${cpugraph 20}
Load: $alignr $loadavg
Processes: $alignr $processes
Running: $alignr $running_processes
RAM: $alignr $mem/$memmax
${membar 3}
Swap: $alignr $swap / $swapmax
${swapbar 3}
$stippled_hr
Name $alignr PID     CPU%   MEM%
${color #ddaa00} ${top name 1} $alignr ${top pid 1} ${top cpu 1} ${top mem 1}$color
${top name 2} $alignr ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3} ${top mem 3}

Mem usage$color
${color #ddaa00} ${top_mem name 1} $alignr ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}$color
${top_mem name 2} $alignr ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${top_mem name 3} $alignr ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
$stippled_hr
${color #ddaa00} CPU:  ${alignr} ${acpitemp}C$color
GPU:$alignr${execi 30 nvidia-settings -q [gpu:0]/GPUCoreTemp | grep '):' | awk '{print $4}' | sed 's/\.//'}C
$stippled_hr
ROOT: $alignr ${fs_free /} / ${fs_size /}
${fs_bar 3 /}
HOME: $alignr ${fs_free /home} / ${fs_size /home}
${fs_bar 3 /home}
XDATA: $alignr ${fs_free /mnt/xdata} / ${fs_size /mnt/xdata}
${fs_bar 3 /mnt/xdata}
$stippled_hr
I/O:
Write: $alignr $diskio_write
${diskiograph_write /dev/sda 20}
Read: $alignr $diskio_read
${diskiograph_read /dev/sda 20}
$stippled_hr
Down ${downspeed eth0} k/s ${alignc}     eth0 ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107} ${alignr}${upspeedgraph eth0 25,107}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

Down ${downspeed eth1} k/s ${alignc}     eth1 ${alignr}Up ${upspeed eth1} k/s
${downspeedgraph eth1 25,107} ${alignr}${upspeedgraph eth1 25,107}
Total ${totaldown eth1} ${alignr}Total ${totalup eth1}

${rss [http://milw0rm.com/rss.php](http://milw0rm.com/rss.php) 60 item_titles 10}
${rss [http://www.securityfocus.com/rss/vulnerabilities.xml](http://www.securityfocus.com/rss/vulnerabilities.xml) 60 item_titles 10}[I][B]i saved this and added conky to startup applications
i selected the file from "/user/bin" file name was conky 

and rebooted the system but it isn't working 

can any one explain me where m wrong ???

m using the latest ubuntu version

i followed this tut - [http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html)

and tried the one from this forum also the how to one :


but cant figure it out


waiting for reply :)[/B][/I]

---

### Post by DaveAU on 2009-05-16
The file you're meant to edit is .conkyrc - dot files are semi-hidden files for user preferences etc - and it needs to be stored in your home folder - ie, you need to put your conky configuration in /home/[user name here]/.conkyrc

While you're at it, if you're going to be tuning your conky configuration a bit (or if you get sick of killing the conky process and restarting everytime you make a change), you can make it reload the .conkyrc with:
> killall -SIGHUP conky

Hope this helps.

---

### Post by binbash on 2009-05-16
you can follow my step by step howto : [http://www.ubuntu-inside.me/2009/05/howto-set-up-conky-on-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/05/howto-set-up-conky-on-ubuntu-jaunty.html)

---

