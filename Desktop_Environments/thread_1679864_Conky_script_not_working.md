---
title: "Conky script not working"
date: 2011-02-01
forum: Desktop Environments
---

### Post by MichaelGld on 2011-02-01
This is the first time I have tried this. I am trying to run a script that runs at startup. I have followed directions found at this Website: [http://www.webupd8.org/2009/05/how-to-install-and-configure-conky.html]("http://www.webupd8.org/2009/05/how-to-install-and-configure-conky.html")
Everything works except the script which consists of two lines.

#!/bin/bash
sleep 30 && conky ;

I changed the file permissions to be executed and named it [FONT="Courier New"].conky-startup.sh[/FONT]. 

Then I went to System>Preferences>Startup Applications and created a new entry that points to my script file. When I restarted my system, Conky didn't start. If I try to run the file from Nautilus or the Terminal, nothing happens.

Thanks for any ideas on this.

---

### Post by wilee-nilee on 2011-02-01
Are those two lines in a gedit, and in home where it is linked to the startup manager.

---

### Post by MichaelGld on 2011-02-01
Yes, I used gedit to create the file. The file is located in /home/mike. I used the browse function in startup manager to select the file. But remember, the file doesn't even run when I type it in at the Terminal.

Just now, I killed Conky from the command prompt, then typed "./conkystart.sh" and I got the following response:










mike@mike-desktop:~$ ./conkystart.sh
[COLOR="Red"]Conky: /home/ubuntuadmin/.conkyrc: 39: no such configuration:[/COLOR] 'border_margin'
Conky: one or more $endif's are missing
Conky: forked to background, pid is 4016
mike@mike-desktop:~$ 
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  20 (X_GetProperty)
  Resource id in failed request:  0x1a228e2
  Serial number of failed request:  252
  Current serial number in output stream:  252

I notice that the first line has a directory path that doesn't exist. Perhaps when I configured conky-colors, I didn't tell it the proper path?

Thanks

---

### Post by nick_goodfate on 2011-02-01
> **MichaelGld said:**
> Yes, I used gedit to create the file. The file is located in /home/mike. I used the browse function in startup manager to select the file. But remember, the file doesn't even run when I type it in at the Terminal.

Just now, I killed Conky from the command prompt, then typed "./conkystart.sh" and I got the following response:

mike@mike-desktop:~$ ./conkystart.sh
[COLOR="Red"]Conky: /home/ubuntuadmin/.conkyrc: 39: no such configuration:[/COLOR] 'border_margin'
Conky: one or more $endif's are missing
Conky: forked to background, pid is 4016
mike@mike-desktop:~$ 
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  20 (X_GetProperty)
  Resource id in failed request:  0x1a228e2
  Serial number of failed request:  252
  Current serial number in output stream:  252

I notice that the first line has a directory path that doesn't exist. Perhaps when I configured conky-colors, I didn't tell it the proper path?

Thanks

Can you post your conkyrc here(/home/mike/.conkyrc . Ctrl+H to see hidden files like this one)?

---

### Post by MichaelGld on 2011-02-01
Here it is.

######################
# - Conky settings - #
######################
update_interval 1
total_run_times 0
net_avg_samples 1
cpu_avg_samples 1

imlib_cache_size 0
double_buffer yes
no_buffers yes

format_human_readable

#####################
# - Text settings - #
#####################
use_xft yes
xftfont Droid Sans:size=8
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################
own_window_class Conky
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

alignment top_right
gap_x 25
gap_y 40
minimum_size 182 0
maximum_width 182

default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color cccccc

color0 white
color1 E07A1F
color2 white

TEXT
${font Droid Sans:style=Bold:size=8}SYSTEM $stippled_hr${font}
##############
# - SYSTEM - #
##############
${color0}${voffset 6}${font OpenLogos:size=19}u${font}${color}${goto 32}${voffset -14}Kernel:  ${alignr}${color2}${kernel}${color}
${goto 32}Uptime: ${alignr}${color2}${uptime}${color}
# |--UPDATES
${goto 32}Updates: ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 360 aptitude search "~U" | wc -l | tail}${color}${font} ${color2}Packages${color}
# |--CPU
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -16}${goto 32}CPU1: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu1}%${font} ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 30 sensors | grep 'Core 0' | cut -c15-16}°C${color}${font}  ${color2}${cpugraph cpu1 8,50 CE5C00 E07A1F}${color}
${goto 32}CPU2: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu2}%${font} ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 30 sensors | grep 'Core 1' | cut -c15-16}°C${color}${font}  ${color2}${cpugraph cpu2 8,50 CE5C00 E07A1F}${color}
# |--MEM
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Droid Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 2}${color0}${membar 4,18}${color}${goto 32}${voffset -2}F: ${font Droid Sans:style=Bold:size=8}${color2}${memeasyfree}${color}${font} U: ${font Droid Sans:style=Bold:size=8}${color2}${mem}${color}${font}
# |--CPU
${voffset 2}${color0}${font Poky:size=14}s${font}${color}${voffset -8}${goto 32}SWAP: ${font Droid Sans:style=Bold:size=8}${color1}${swapperc}%${color}${font}
${voffset 4}${offset 1}${color0}${swapbar 4,18}${color}${voffset -4}${goto 32}F: ${font Droid Sans:style=Bold:size=8}${color2}$swapmax${color}${font} U: ${font Droid Sans:style=Bold:size=8}${color2}$swap${color}${font}
# |--PROC
${voffset 2}${color0}${font Poky:size=15}a${font}${color}${goto 32}${voffset -10}Processes: ${color2}${alignr 13}CPU${alignr}RAM${color}
${voffset -1}${goto 42}${color2}${top name 1}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 1}${alignr }${top mem 1}${color}${font}
${voffset -1}${goto 42}${color2}${top name 2}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 2}${alignr }${top mem 2}${color}${font}
${voffset -1}${goto 42}${color2}${top name 3}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 3}${alignr }${top mem 3}${color}${font}
${voffset -1}${goto 42}${color2}${top name 4}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 4}${alignr }${top mem 4}${color}${font}
${voffset -1}${goto 42}${color2}${top name 5}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 5}${alignr }${top mem 5}${color}${font}
#############
# - CLOCK - #
#############
${voffset 4}${font Droid Sans:style=Bold:size=8}DATE $stippled_hr${font}
${voffset -10}${alignc 46}${color2}${font Arial Black:size=30}${time %H:%M}${font}${color}
${alignc}${time %d %B %Y}
##########
# - HD - #
##########
${voffset 4}${font Droid Sans:style=Bold:size=8}HD $stippled_hr${font}
${execpi 30 ~/.conkycolors/bin/conkyHD1}
###############
# - NETWORK - #
###############
${voffset 4}${font Droid Sans:style=Bold:size=8}NETWORK $stippled_hr${font}
# |--WLAN0
${if_up wlan0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} ${alignr}${color2}${upspeedgraph wlan0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup wlan0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} ${alignr}${color2}${downspeedgraph wlan0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown wlan0}${color}${font}
${voffset -2}${color0}${font Poky:size=14}Y${font}${color}${goto 32} ${voffset -2}Signal: ${font Droid Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -8}Local IP: ${alignr}${color2}${addr wlan0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--ETH0
${else}${if_up eth0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} ${alignr}${color2}${upspeedgraph eth0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup eth0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} ${alignr}${color2}${downspeedgraph eth0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown eth0}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr eth0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--PPP0
${else}${if_up ppp0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} ${alignr}${color2}${upspeedgraph ppp0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup ppp0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} ${alignr}${color2}${downspeedgraph ppp0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown ppp0}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr ppp0}${color}
${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Network Unavailable${voffset 14}${endif}${endif}${endif}

---

### Post by stinkeye on 2011-02-01
I don't know if it was a copy and paste error but the config you posted
has a number of errors in it with spaces where they shouldn't be.
eg```
${c[COLOR="Red"]o l[/COLOR]or}${font} U: ${font Droid Sans:style=Bold:size=8}${color2}${mem}${color}${f[COLOR="#ff0000"]o n[/COLOR]t}
```


Save this as **.conkyrc** in your home folder
```
######################
# - Conky settings - #
######################
update_interval 1
total_run_times 0
net_avg_samples 1
cpu_avg_samples 1

imlib_cache_size 0
double_buffer yes
no_buffers yes

format_human_readable

#####################
# - Text settings - #
#####################
use_xft yes
xftfont Droid Sans:size=8
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################
own_window_class Conky
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

alignment top_right
gap_x 25
gap_y 40
minimum_size 182 0
maximum_width 182

default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color cccccc

color0 white
color1 E07A1F
color2 white

TEXT
${font Droid Sans:style=Bold:size=8}SYSTEM $stippled_hr${font}
##############
# - SYSTEM - #
##############
${color0}${voffset 6}${font OpenLogos:size=19}u${font}${color}${goto 32}${voffset -14}Kernel: ${alignr}${color2}${kernel}${color}
${goto 32}Uptime: ${alignr}${color2}${uptime}${color}
# |--UPDATES
${goto 32}Updates: ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 360 aptitude search "~U" | wc -l | tail}${color}${font} ${color2}Packages${color}
# |--CPU
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -16}${goto 32}CPU1: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu1}%${font} ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 30 sensors | grep 'Core 0' | cut -c15-16}°C${color}${font} ${color2}${cpugraph cpu1 8,50 CE5C00 E07A1F}${color}
${goto 32}CPU2: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu2}%${font} ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 30 sensors | grep 'Core 1' | cut -c15-16}°C${color}${font} ${color2}${cpugraph cpu2 8,50 CE5C00 E07A1F}${color}
# |--MEM
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Droid Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 2}${color0}${membar 4,18}${color}${goto 32}${voffset -2}F: ${font Droid Sans:style=Bold:size=8}${color2}${memeasyfree}${color}${font} U: ${font Droid Sans:style=Bold:size=8}${color2}${mem}${color}${font}
# |--CPU
${voffset 2}${color0}${font Poky:size=14}s${font}${color}${voffset -8}${goto 32}SWAP: ${font Droid Sans:style=Bold:size=8}${color1}${swapperc}%${color}${font}
${voffset 4}${offset 1}${color0}${swapbar 4,18}${color}${voffset -4}${goto 32}F: ${font Droid Sans:style=Bold:size=8}${color2}$swapmax${color}${font} U: ${font Droid Sans:style=Bold:size=8}${color2}$swap${color}${font}
# |--PROC
${voffset 2}${color0}${font Poky:size=15}a${font}${color}${goto 32}${voffset -10}Processes: ${color2}${alignr 13}CPU${alignr}RAM${color}
${voffset -1}${goto 42}${color2}${top name 1}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 1}${alignr }${top mem 1}${color}${font}
${voffset -1}${goto 42}${color2}${top name 2}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 2}${alignr }${top mem 2}${color}${font}
${voffset -1}${goto 42}${color2}${top name 3}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 3}${alignr }${top mem 3}${color}${font}
${voffset -1}${goto 42}${color2}${top name 4}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 4}${alignr }${top mem 4}${color}${font}
${voffset -1}${goto 42}${color2}${top name 5}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 5}${alignr }${top mem 5}${color}${font}
#############
# - CLOCK - #
#############
${voffset 4}${font Droid Sans:style=Bold:size=8}DATE $stippled_hr${font}
${voffset -10}${alignc 46}${color2}${font Arial Black:size=30}${time %H:%M}${font}${color}
${alignc}${time %d %B %Y}
##########
# - HD - #
##########
${voffset 4}${font Droid Sans:style=Bold:size=8}HD $stippled_hr${font}
${execpi 30 ~/.conkycolors/bin/conkyHD1}
###############
# - NETWORK - #
###############
${voffset 4}${font Droid Sans:style=Bold:size=8}NETWORK $stippled_hr${font}
# |--WLAN0
${if_up wlan0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} ${alignr}${color2}${upspeedgraph wlan0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup wlan0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} ${alignr}${color2}${downspeedgraph wlan0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown wlan0}${color}${font}
${voffset -2}${color0}${font Poky:size=14}Y${font}${color}${goto 32} ${voffset -2}Signal: ${font Droid Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -8}Local IP: ${alignr}${color2}${addr wlan0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--ETH0
${else}${if_up eth0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} ${alignr}${color2}${upspeedgraph eth0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup eth0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} ${alignr}${color2}${downspeedgraph eth0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown eth0}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr eth0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--PPP0
${else}${if_up ppp0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} ${alignr}${color2}${upspeedgraph ppp0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup ppp0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} ${alignr}${color2}${downspeedgraph ppp0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown ppp0}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr ppp0}${color}
${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Network Unavailable${voffset 14}${endif}${endif}${endif}
```


> I changed the file permissions to be executed and named it **.conky-startup.sh**.
> Just now, I killed Conky from the command prompt, then typed "**./conkystart.sh**" and I got the following response:

If you saved the startup script as **.conky-startup.sh** in your home folder, then the 
command to run it is
```
./.conky-startup.sh
```with the preceding dot.

I tested the startup script with a reboot and it runs fine here.
You should have a startup script in your **~/.conkycolors/bin** folder anyway.

---

### Post by MichaelGld on 2011-02-02
> **stinkeye said:**
> I don't know if it was a copy and paste error but the config you posted
has a number of errors in it with spaces where they shouldn't be.
eg```
${c[COLOR="Red"]o l[/COLOR]or}${font} U: ${font Droid Sans:style=Bold:size=8}${color2}${mem}${color}${f[COLOR="#ff0000"]o n[/COLOR]t}
```
[INDENT]I'll check it, but if it's not a copy and paste error, how would I fit it?[/INDENT]

Save this as **.conkyrc** in your home folder
```
######################
# - Conky settings - #
######################
update_interval 1
total_run_times 0
net_avg_samples 1
cpu_avg_samples 1

imlib_cache_size 0
double_buffer yes
no_buffers yes

format_human_readable

#####################
# - Text settings - #
#####################
use_xft yes
xftfont Droid Sans:size=8
override_utf8_locale yes
text_buffer_size 2048

#############################
# - Window specifications - #
#############################
own_window_class Conky
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

alignment top_right
gap_x 25
gap_y 40
minimum_size 182 0
maximum_width 182

default_bar_size 60 8

#########################
# - Graphics settings - #
#########################
draw_shades no

default_color cccccc

color0 white
color1 E07A1F
color2 white

TEXT
${font Droid Sans:style=Bold:size=8}SYSTEM $stippled_hr${font}
##############
# - SYSTEM - #
##############
${color0}${voffset 6}${font OpenLogos:size=19}u${font}${color}${goto 32}${voffset -14}Kernel: ${alignr}${color2}${kernel}${color}
${goto 32}Uptime: ${alignr}${color2}${uptime}${color}
# |--UPDATES
${goto 32}Updates: ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 360 aptitude search "~U" | wc -l | tail}${color}${font} ${color2}Packages${color}
# |--CPU
${offset 1}${color0}${font Poky:size=16}P${font}${offset -19}${voffset 9}${cpubar cpu0 4,18}${color}${voffset -16}${goto 32}CPU1: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu1}%${font} ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 30 sensors | grep 'Core 0' | cut -c15-16}°C${color}${font} ${color2}${cpugraph cpu1 8,50 CE5C00 E07A1F}${color}
${goto 32}CPU2: ${font Droid Sans:style=Bold:size=8}${color1}${cpu cpu2}%${font} ${alignr}${font Droid Sans:style=Bold:size=8}${color1}${execi 30 sensors | grep 'Core 1' | cut -c15-16}°C${color}${font} ${color2}${cpugraph cpu2 8,50 CE5C00 E07A1F}${color}
# |--MEM
${color0}${font Poky:size=16}M${font}${color}${goto 32}${voffset -7}RAM: ${font Droid Sans:style=Bold:size=8}${color1}$memperc%${color}${font}
${offset 1}${voffset 2}${color0}${membar 4,18}${color}${goto 32}${voffset -2}F: ${font Droid Sans:style=Bold:size=8}${color2}${memeasyfree}${color}${font} U: ${font Droid Sans:style=Bold:size=8}${color2}${mem}${color}${font}
# |--CPU
${voffset 2}${color0}${font Poky:size=14}s${font}${color}${voffset -8}${goto 32}SWAP: ${font Droid Sans:style=Bold:size=8}${color1}${swapperc}%${color}${font}
${voffset 4}${offset 1}${color0}${swapbar 4,18}${color}${voffset -4}${goto 32}F: ${font Droid Sans:style=Bold:size=8}${color2}$swapmax${color}${font} U: ${font Droid Sans:style=Bold:size=8}${color2}$swap${color}${font}
# |--PROC
${voffset 2}${color0}${font Poky:size=15}a${font}${color}${goto 32}${voffset -10}Processes: ${color2}${alignr 13}CPU${alignr}RAM${color}
${voffset -1}${goto 42}${color2}${top name 1}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 1}${alignr }${top mem 1}${color}${font}
${voffset -1}${goto 42}${color2}${top name 2}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 2}${alignr }${top mem 2}${color}${font}
${voffset -1}${goto 42}${color2}${top name 3}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 3}${alignr }${top mem 3}${color}${font}
${voffset -1}${goto 42}${color2}${top name 4}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 4}${alignr }${top mem 4}${color}${font}
${voffset -1}${goto 42}${color2}${top name 5}${color}${font Droid Sans:style=Bold:size=8}${color1} ${goto 124}${top cpu 5}${alignr }${top mem 5}${color}${font}
#############
# - CLOCK - #
#############
${voffset 4}${font Droid Sans:style=Bold:size=8}DATE $stippled_hr${font}
${voffset -10}${alignc 46}${color2}${font Arial Black:size=30}${time %H:%M}${font}${color}
${alignc}${time %d %B %Y}
##########
# - HD - #
##########
${voffset 4}${font Droid Sans:style=Bold:size=8}HD $stippled_hr${font}
${execpi 30 ~/.conkycolors/bin/conkyHD1}
###############
# - NETWORK - #
###############
${voffset 4}${font Droid Sans:style=Bold:size=8}NETWORK $stippled_hr${font}
# |--WLAN0
${if_up wlan0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed wlan0}${color}${font} ${alignr}${color2}${upspeedgraph wlan0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup wlan0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed wlan0}${color}${font} ${alignr}${color2}${downspeedgraph wlan0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown wlan0}${color}${font}
${voffset -2}${color0}${font Poky:size=14}Y${font}${color}${goto 32} ${voffset -2}Signal: ${font Droid Sans:style=Bold:size=8}${color1}${wireless_link_qual wlan0}%${color}${font} ${alignr}${color2}${wireless_link_bar 8,60 wlan0}${color}
${voffset 4}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -8}Local IP: ${alignr}${color2}${addr wlan0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--ETH0
${else}${if_up eth0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed eth0}${color}${font} ${alignr}${color2}${upspeedgraph eth0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup eth0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed eth0}${color}${font} ${alignr}${color2}${downspeedgraph eth0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown eth0}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr eth0}${color}
${goto 32}Public IP: ${alignr}${color2}${execi 10800 ~/.conkycolors/bin/conkyIp}${color}
# |--PPP0
${else}${if_up ppp0}
${voffset -13}${color0}${font VariShapes Solid:size=14}q${font}${color}${goto 32}${voffset -6}Up: ${font Droid Sans:style=Bold:size=8}${color1}${upspeed ppp0}${color}${font} ${alignr}${color2}${upspeedgraph ppp0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totalup ppp0}${color}${font}
${voffset -2}${color0}${font VariShapes Solid:size=14}Q${font}${color}${goto 32}${voffset -6}Down: ${font Droid Sans:style=Bold:size=8}${color1}${downspeed ppp0}${color}${font} ${alignr}${color2}${downspeedgraph ppp0 8,60 CE5C00 E07A1F}${color}
${goto 32}Total: ${font Droid Sans:style=Bold:size=8}${color2}${totaldown ppp0}${color}${font}
${voffset -2}${color0}${font Poky:size=13}w${font}${color}${goto 32}${voffset -4}Local IP: ${alignr}${color2}${addr ppp0}${color}
${else}${voffset 4}${color0}${font PizzaDude Bullets:size=12}4${font}${color}${goto 32}Network Unavailable${voffset 14}${endif}${endif}${endif}
```





If you saved the startup script as **.conky-startup.sh** in your home folder, then the 
command to run it is
```
./.conky-startup.sh
```with the preceding dot.

I tested the startup script with a reboot and it runs fine here.
You should have a startup script in your **~/.conkycolors/bin** folder anyway.

When I turned on my system this morning, Conky was there. I had tinkered a little bit (but not your suggestions - I hadn't seen them yet) before I shut down last night. Can't remember what it was right now, but it worked. Thanks to all for your help.

---

