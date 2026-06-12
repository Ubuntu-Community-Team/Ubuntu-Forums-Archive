---
title: "conky :("
date: 2011-05-20
forum: Desktop Environments
---

### Post by kasrawis on 2011-05-20
naseer@naseer:~$ conky
Conky: /home/naseer/.conkyrc: 36: no such configuration: 'border_margin'
Conky: statfs '/home/tmo': No such file or directory
Conky: desktop window (1a000ad) is subwindow of root window (ac)
Conky: window type - override
Conky: drawing to created window (0x3e00001)
Conky: drawing to double buffer
Conky: statfs '/home/tmo': No such file or directory
Conky: can't open /sys/class/power_supply/6/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/6/state: No such file or directory
Conky: obj->data.i 2 info.cpu_count 1
Conky: attempting to use more CPUs than you have!
naseer@naseer:~$ 

after installation complete i paste some codes in terminal i typed conky i got above what does it mean 

my system 
1.6 
512
128 shared memory

---

### Post by ajgreeny on 2011-05-20
> **kasrawis said:**
> naseer@naseer:~$ conky
Conky: /home/naseer/.conkyrc: 36: no such configuration: 'border_margin'
Conky: statfs '/home/tmo': No such file or directory
Conky: desktop window (1a000ad) is subwindow of root window (ac)
Conky: window type - override
Conky: drawing to created window (0x3e00001)
Conky: drawing to double buffer
Conky: statfs '/home/tmo': No such file or directory
Conky: can't open /sys/class/power_supply/6/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/6/state: No such file or directory
Conky: obj->data.i 2 info.cpu_count 1
Conky: attempting to use more CPUs than you have!
naseer@naseer:~$ 

after installation complete i paste some codes in terminal i typed conky i got above what does it mean 

my system 
1.6 
512
128 shared memory
The .conkyrc configuration file is pointing to a folder in /home, and therefore another user called **tmo**, and can not find that user.

There is also no battery state monitor file to use, and finally you are expecting to see info from a twin core cpu, but it looks as if you have a single core cpu instead.

Can you copy back here the output of ```
cat .conkyrc
``` and ```
ls /home
```which may help.

---

### Post by kasrawis on 2011-05-22
```
naseer@naseer:~$ cat .conkyrc
# UBUNTU-CONKY
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 200 800

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

text_buffer_size 1024

# stuff after ‘TEXT’ will be formatted on screen

TEXT
$color${font arial:size=9}
$nodename@$sysname $kernel on $machine${font arial:size=8}
Battery ${battery_bar 6 BAT0}

${color orange}CPU $color
${freq}MHz${alignr}Load: ${loadavg}
${alignr}${loadgraph 20,250 e5e5e5 F1AA0E}
CPU Total:${color} ${cpu cpu0}% ${color}${alignr}Temp:${color} ${acpitemp}
${alignr}${cpugraph 0 20,250 e5e5e5 F1AA0E}
Core one: ${color}${cpu cpu1}% ${alignr} Core two: ${color}${cpu cpu2}%
${cpugraph 1 20,120 e5e5e5 F1AA0E}${alignr}${cpugraph 2 20,120 e5e5e5 F1AA0E}
NAME${alignr}PID         CPU%        MEM%
${top name 1}${alignr}${top pid 1}       ${top cpu 1}          ${top mem 1}     

${color orange}MEMORY / DISK $color
Total: ${color}${memmax} ${alignr} Free: ${color}${memfree}
RAM: $memperc% ${alignr}Swap: $swapperc% 
${memgraph 20,120 e5e5e5 F1AA0E} ${alignr} ${swapbar 20,120 }
root: ${fs_used_perc /}% ${fs_bar 6 /}$color
home: ${fs_used_perc /home/tmo}% ${fs_bar 6 /home/tmo}$color

${color orange}WIFI (${addr wlan0}) $color
${wireless_essid wlan0} ${wireless_link_bar 6 wlan0}
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 20,120 e5e5e5 F1AA0E} ${alignr}${upspeedgraph wlan0
20,120 e5e5e5 F1AA0E}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING $color
${font arial:size=7}${execi 30 tail -n 10 /var/log/messages | fold -w45}
naseer@naseer:~$ 

```

```
naseer@naseer:~$ ls /home
naseer
naseer@naseer:~$
```

Thanks for helping me

---

### Post by Robicika on 2011-05-22
Try this:  [http://code.google.com/p/conkywizard/downloads/list](http://code.google.com/p/conkywizard/downloads/list)

---

### Post by ManualSparrow on 2011-05-22
You are also trying to call on the second processor when there is only one apparently, so delete that part of the config file.

---

### Post by kasrawis on 2011-05-23
> **ManualSparrow said:**
> You are also trying to call on the second processor when there is only one apparently, so delete that part of the config file.

yes i did delete that part and still same error actually i deleted that part before posting here :) thanks anyway i'm gonna check from here [http://code.google.com/p/conkywizard/downloads/list](http://code.google.com/p/conkywizard/downloads/list)

---

### Post by Copper Bezel on 2011-05-23
The calls to /home/tmo are in the .conkyrc, too. Where did you get this .conkyrc? Whoever uploaded it wasn't paying much attention.

---

### Post by kasrawis on 2011-05-23
thank you all very very much for you help 1 more final thing where .conkyrc is? i'm on Xubuntu 11.04 i couldn't find it at my Home folder(i showed hiddens files Ctrl+H) 

and where to get like this themes [http://code.google.com/p/conkywizard/downloads/list](http://code.google.com/p/conkywizard/downloads/list)
 
if there is no more theme where to get scrips and where to paste them ? 

thanks 

i'm new with these conky stuffs

---

### Post by Robicika on 2011-05-23
The conkyWizard is a little help to customize you're conky, but the problem is that you cant do too much.  You can change the config file, but I recommend to read about conky config file customization. It is not too hard to understand the basic things.  to open the conkyWizard config file type in terminal:  gedit .ConkyWizardTheme/ConkyWizardTheme (or : kate .ConkyWizardTheme/ConkyWizardTheme           for KDE)  You can practice on this and than write your own configuration.  Good luck!

---

