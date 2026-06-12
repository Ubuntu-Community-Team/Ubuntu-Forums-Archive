---
title: "stupid conky problem!"
date: 2008-01-10
forum: Desktop Effects &amp; Customization
---

### Post by x3roconf on 2008-01-10
When i log in Conky window flashes and goes away but conky is still running? Why it goes away?

My .conkyrc

```

background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_spacer yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.5
update_interval 1.0
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
own_window_colour brown
own_window_transparent yes
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 25
# Subtract file system buffers from used memory?
no_buffers yes


#  FOR MY INFO
# For international dates & times ${tztime} see: /usr/share/zoneinfo
# Leave 3 blank lines below TEXT to clear panels
# add this line below TEXT to test things, remove when finished.

#${color cyan}Setup: Weather$color
#${color cyan}Fix me: CPU Temp: ${color white}${acpitemp}C $color
#${color red}Test Cmds Above ${hr 3} $color

TEXT

${alignc}${color cyan}~~== ${color orange}GMT ${color white}${tztime GMT 
%H:%M:%S} ${color cyan}==~~$color
${alignc}${Color orange}~~== ${color cyan}Canada ${color 
orange}==~~$color
${color orange}Sis${alignr}${color cyan}Winnipeg${color cyan}: ${color 
white}${tztime Canada/Central %H:%M:%S}$color
${color orange}JBM & CDM & LilSis${alignr}${alignr}${color 
cyan}London${color cyan}: ${color white}${tztime Canada/Eastern 
%H:%M:%S}$color

${alignc}${Color orange}~~== ${color cyan}Buenos Aires ${color 
orange}==~~$color

${color white}${alignc}${time %A, %d %b. %y} ${color cyan}: ${color 
white}${time %H:%M:%S}
${color orange}${alignc}$sysname $kernel ($machine)
${color orange}${alignc}UpTime for ${color white}${exec whoami} @ 
$nodename${color orange} $uptime $color
${color cyan}${hr 1}$color
${color orange}CPU: ${color white}${cpu}% ${color orange}${cpubar cpu0} 
$color
${color cyan}Freq: ${color white}$freq ${color cyan}MHz ${color cyan}     
Running: ${color white}$running_processes ${color cyan}of ${color 
white}$processes${color cyan}processes $color
${color cyan}Load Avg (${color yellow}Min${color cyan}):$alignr${color 
yellow}1: ${color white}${loadavg 1}      ${color yellow}5: ${color 
white}${loadavg 2}     ${color yellow}15: ${color white}${loadavg 3} 
${color orange}$color

${color orange}MEM: ${color cyan}RAM: ${color white}$memperc% ${color 
cyan}(${color white}${mem} ${color cyan}of ${color 
orange}${memmax}${color cyan}) ${color orange}$membar $color
${color orange}DISK: ${color cyan}Swap: ${color white}$swapperc% ${color 
cyan}(${color white}${swap} ${color cyan}of ${color 
orange}${swapmax}${color cyan})${color orange} ${swapbar}$color

${color orange}HD Info ${hr 1} $color
${color cyan}Ubuntu (sda5):${alignr}${color white}${fs_free_perc 
/media/sda5}% ${color cyan}(${color white}${fs_used /media/sda5} ${color 
cyan}of ${color orange}${fs_size /media/sda5}${color cyan}) $color
${color cyan}W2K (sda1):${alignr}${color white}${fs_free_perc 
/media/sda1}% ${color cyan}(${color white}${fs_used /media/sda1} ${color 
cyan}of ${color orange}${fs_size /media/sda1}${color cyan}) $color
${color orange}${hr 1} $color
${color cyan}BruLoo (sdb1):${alignr}${color white}${fs_free_perc 
/media/sdb1}% ${color cyan}(${color white}${fs_used /media/sdb1} ${color 
cyan}of ${color orange}${fs_size /media/sdb1}${color cyan}) $color
${color orange}${hr 1} $color
${color orange}IP ${color cyan}(${color white}${addr eth0}${color cyan}) 
${color orange}${hr 1} $color
${color cyan}Down: ${color white}${downspeed eth0}k/s ${alignr}${color 
cyan}Up: ${color white}${upspeed eth0}k/s $color
${color cyan}Total: ${color white}${totaldown eth0} ${alignr}${color 
cyan}Total: ${color white}${totalup eth0} $color
${color cyan}Inbound: ${color white}$background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_spacer yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.5
update_interval 1.0
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
own_window_colour brown
own_window_transparent yes
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 25
# Subtract file system buffers from used memory?
no_buffers yes


#  FOR MY INFO
# For international dates & times ${tztime} see: /usr/share/zoneinfo
# Leave 1 blank line below TEXT to clear panel
# add this line below TEXT to test things, remove when finished.

#${color cyan}NOT working: CPU Temp: ${color white}${acpitemp}C $color
#Find out HowTo: HD Temps
#${color red}Test Cmds Above ${hr 3} $color

TEXT

${alignc}${color cyan}~~== ${color orange}GMT ${color white}${tztime GMT 
%H:%M:%S} ${color cyan}==~~$color
${alignc}${Color orange}~~== ${color cyan}Canada ${color 
orange}==~~$color
${color orange}Sis${alignr}${color cyan}Winnipeg${color cyan}: ${color 
white}${tztime Canada/Central %H:%M:%S}$color
${color orange}JBM & CDM & LilSis${alignr}${alignr}${color 
cyan}London${color cyan}: ${color white}${tztime Canada/Eastern 
%H:%M:%S}$color

${alignc}${Color orange}~~== ${color cyan}Buenos Aires ${color 
orange}==~~$color
h
${color white}${alignc}${time %A, %d %b. %y} ${color cyan}: ${color 
white}${time %H:%M:%S}
${color orange}${alignc}$sysname $kernel ($machine)
${color orange}${alignc}UpTime for ${color white}${exec whoami} @ 
$nodename${color orange} $uptime $color
${color cyan}${hr 1}$color
${color orange}CPU: ${color white}${cpu}% ${color orange}${cpubar cpu0} 
$color
${color cyan}Freq: ${color white}$freq ${color cyan}MHz ${color cyan}     
Running: ${color white}$running_processes ${color cyan}of ${color 
white}$processes${color cyan}processes $color
${color cyan}Load Avg (${color yellow}Min${color cyan}):$alignr${color 
yellow}1: ${color white}${loadavg 1}      ${color yellow}5: ${color 
white}${loadavg 2}     ${color yellow}15: ${color white}${loadavg 3} 
${color orange}$color

${color orange}MEM: ${color cyan}RAM: ${color white}$memperc% ${color 
cyan}(${color white}${mem} ${color cyan}of ${color 
orange}${memmax}${color cyan}) ${color orange}$membar $color
${color orange}DISK: ${color cyan}Swap: ${color white}$swapperc% ${color 
cyan}(${color white}${swap} ${color cyan}of ${color 
orange}${swapmax}${color cyan})${color orange} ${swapbar}$color

${color orange}HD Info ${hr 1} $color
${color cyan}Ubuntu (sda5):${alignr}${color white}${fs_free_perc 
/media/sda5}% ${color cyan}(${color white}${fs_used /media/sda5} ${color 
cyan}of ${color orange}${fs_size /media/sda5}${color cyan}) $color
${color cyan}W2K (sda1):${alignr}${color white}${fs_free_perc 
/media/sda1}% ${color cyan}(${color white}${fs_used /media/sda1} ${color 
cyan}of ${color orange}${fs_size /media/sda1}${color cyan}) $color
${color orange}${hr 1} $color
${color cyan}BruLoo (sdb1):${alignr}${color white}${fs_free_perc 
/media/sdb1}% ${color cyan}(${color white}${fs_used /media/sdb1} ${color 
cyan}of ${color orange}${fs_size /media/sdb1}${color cyan}) $color
${color orange}${hr 1} $color
${color orange}IP ${color cyan}(${color white}${addr eth0}${color cyan}) 
${color orange}${hr 1} $color
${color cyan}Down: ${color white}${downspeed eth0}k/s ${alignr}${color 
cyan}Up: ${color white}${upspeed eth0}k/s $color
${color cyan}Total: ${color white}${totaldown eth0} ${alignr}${color 
cyan}Total: ${color white}${totalup eth0} $color
${color cyan}Inbound: ${color white}${tcp_portmon 1 32767 count}          
${color cyan}Outbound: ${color white}${tcp_portmon 32768 61000 
count}${alignr}${color cyan}Total: ${color white}${tcp_portmon 1 65535 
count} $color
${color orange}Connections ${color white}${tcp_portmon 32768 61000 
count} ${alignr} ${color orange}Service/Port $color${color white}
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 
rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 
rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 
rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 
rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 
rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 
rservice 5}$color{tcp_portmon 1 32767 count}          ${color 
cyan}Outbound: ${color white}${tcp_portmon 32768 61000 
count}${alignr}${color cyan}Total: ${color white}${tcp_portmon 1 65535 
count} $color
${color orange}Connections ${color white}${tcp_portmon 32768 61000 
count} ${alignr} ${color orange}Service/Port $color${color white}
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 
rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 
rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 
rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 
rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 
rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 
rservice 5}$color

```

---

### Post by notwen on 2008-01-10
Sounds like Compiz/Metacity is starting before conky finishes loading therefore loading over the top of conky.  We'll prevent this by creating a shell script to simply delay conky from starting until Compiz/Metacity are loaded.

```
touch .conkystart
```

```
gedit .conkystart
```

Add the following code into the file and save it:

```
#!/bin/bash
sleep 15 &&
conky &
exit
```

Next lets make our shell script executable:

```
chmod +x .conkystart
```

Now you simply need to add "/home/user/.conkystart" to your startup application and conky will launch every time you start up your PC.  You can change the 15 in .conkystart to whatever works best for your system.  Good luck and hope this helps. =]

---

### Post by x3roconf on 2008-01-10
I got it working. thx!

---

### Post by notwen on 2008-01-10
Good to hear, enjoy modifying your conky configs to no end now. =p

---

