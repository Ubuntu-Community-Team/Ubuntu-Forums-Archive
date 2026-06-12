---
title: "Irritating problem with conky - stays  above desktop"
date: 2011-01-29
forum: Desktop Environments
---

### Post by Mr. ViC on 2011-01-29
This is happening with the new conky config I've got:

[img]http://img.myph.us/VSP.png[/img]

Does anyone have an idea on how to solve this?

By the way, the conky config is this one:

 ```
[http://gnome-look.org/content/show.php/my](http://gnome-look.org/content/show.php/my)+config+Conky?content=120115
```

---

### Post by ajgreeny on 2011-01-29
You give us a link which is most unhelpful; what we need to see is your .conkyrc file, normally in your home.  It is a hidden file, so you may need to use Ctrl+H to see it.

It may also be simply that you have added conky to your startup applications list and it is therefore starting too quickly before the gnome desktop has appeared.  Try changing the command in startup applications from **conky** to **bash -c "sleep 10; conky"** including the quotation marks.

Paste a copy of your .conkyrc file if my suggestion is not effective.

---

### Post by Mr. ViC on 2011-01-29
Hello.

Thanks for helping.

My conky is first located in this folder in home:

[img]http://img.myph.us/Bxx.png[/img]

Inside it, there's this:

[img]http://img.myph.us/xdh.png[/img]

The **startconky_b** code:

```
#!/bin/bash

# Stats Bar
conky -d -c ~/.conky/.conkyrc1B &
conky -d -c ~/.conky/.conkyrc2B

exit
```

The .conkyrc1B code:

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer no
use_xft yes

# Update interval in seconds
update_interval 1

# Minimum size of text area
minimum_size 250

# Draw shades?
draw_shades no

# Text stuff
draw_outline no
# amplifies text if yes
draw_borders yes

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 0

# border margins
border_margin 0

# border width
border_width 0

# Default colors and also border colors, grey90 == #626262
default_color white
default_shade_color black
default_outline_color grey90

own_window_colour 080d14
own_window_transparent yes
own_window_type override

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 0
gap_y 30

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale yes
xftfont Terminus:size=8
xftalpha 0.8

color0    ffffff    #blanco
color1    7da8f8    #
color2    7da8f8    #
color3    7da8f8    #
color4    7da8f8    #
color5    7da8f8    #
color6    ffffff    #titulos
color7    496291    #azul mas oscuro


temperature_unit celsius

TEXT
${voffset 2}${font OpenLogos:size=18}${color6}u${font ArtBrush:Bold:size=14}System ${hr 4}
${voffset -2}${font ArtBrush:size=11}${color1}Host: ${color0}$nodename ${alignr}${color1}Kernel: ${color0}$kernel 
${color1}Time Up: ${color0}$uptime${goto 140}${voffset -8}${font Poky:size=20}${color1}3${font ArtBrush:size=11}${color0}${voffset -9}${battery_percent BAT0}% - ${voffset -5}${font Webdings:size=16}${color1}~${voffset -2}${font ArtBrush:size=11}${color0}${acpiacadapter} 
${voffset -10}
${font Poky:size=18}${color6}a${font ArtBrush:Bold:size=14}CPU ${hr 4}
${voffset -2}${font ArtBrush:size=11}${color2}CPU freq: ${color0}${freq 1}MHz ${alignr}${color2}Temperature: ${color0}${acpitemp}C 
${color1}Processes: ${color0}$processes  ${alignr}${color2}Running: ${color0}$running_processes 
${color2}${cpugraph 30,0 2d3d5a 6b8fd4}
 ${voffset -37}${font ArtBrush:bold:size=20}${color0}$cpu% 
${voffset -10}${color2}${font ArtBrush:size=11}Top Procesos - CPU
${color2} Name  ${goto 105}PID  ${goto 160}CPU  ${goto 210}MEM
${color0} ${top name 1}${goto 100}${top pid 1}${goto 150}${top cpu 1}%${goto 200}${top mem 1}MB
${color2} ${top name 2}${goto 100}${top pid 2}${goto 150}${top cpu 2}%${goto 200}${top mem 2}MB
${color2} ${top name 3}${goto 100}${top pid 3}${goto 150}${top cpu 3}%${goto 200}${top mem 3}MB
${voffset -10}
${font Poky:size=18}${color6}M${font ArtBrush:Bold:size=14}MEMORIA  ${hr 4}
${font ArtBrush:size=11}${color3}Usado: ${color0} $mem ${alignr}${font ArtBrush:bold:size=11}${color3} Swap: ${color0}$swapperc% ${color3}${swapbar 15,101}   
${color3}${memgraph 30,0 2d3d5a 6b8fd4}
 ${voffset -37}${font ArtBrush:bold:size=20}${color0}$memperc%
${voffset -10}${color3}${font ArtBrush:size=11}Top Procesos - RAM
${color3} Name ${goto 210}MEM    
${color0} ${top_mem name 1}${goto 200}${top_mem mem 1}MB 
${color3} ${top_mem name 2}${goto 200}${top_mem mem 2}MB  
${color3} ${top_mem name 3}${goto 200}${top_mem mem 3}MB  
${voffset -10}
${font Poky:size=18}${color6}y${font ArtBrush:Bold:size=14}DISCOS ${hr 4}
${color4}${font ArtBrush:size=11}Read: ${voffset 0}${diskiograph_read 15,90 2d3d5a 6b8fd4} ${voffset 0}${alignr}Write: ${voffset 0}${diskiograph_write 15,90 2d3d5a 6b8fd4}  
                   ${voffset -15}${color0}${diskio_read /dev/sda}${alignr}${diskio_write /dev/sda}   
${color4}${font StyleBats:size=18}F${font ArtBrush:size=11} / ${alignr}(${fs_free /} - ${fs_type /}) ${color4}${fs_bar 15,90 /}  
${voffset -15}${alignr}${color0}${fs_free_perc /}%   
${font StyleBats:size=18}${color4}G${font ArtBrush:size=11} /home ${alignr}(${fs_free /home} - ${fs_type /home}) ${color4}${fs_bar 15,90 /home}  
${voffset -15}${alignr}${color0}${fs_free_perc /home}%   
${if_mounted /media/garoto_dc}${font StyleBats:size=18}${color4}G${font ArtBrush:size=11} 20gb ${alignr}(${fs_free /media/garoto_dc} - ${fs_type /media/garoto_dc}) ${color4}${fs_bar 15,90 /media/garoto_dc}  
${voffset -15}${alignr}${color0}${fs_free_perc /media/garoto_dc}%   
${endif}
${voffset -10}${if_existing /proc/net/route eth0}${color6}${font StyleBats:size=18}M${font ArtBrush:Bold:size=14}WIRED (eth0) ${hr 4}
${color5}${upspeedgraph eth0 20,130 1d273a 6b8fd4} ${downspeedgraph eth0 20,130 1d273a 6b8fd4}
 ${voffset -23}${color0}${font PizzaDude Bullets:size=15}v${font ArtBrush:size=15}${upspeed eth0} ${voffset -1}${alignr}${font PizzaDude Bullets:size=15}r${font ArtBrush:size=15}${downspeed eth0}   
${voffset -2}${font ArtBrush:size=11}${color5}IP local: ${color0}${addr eth0} ${alignr}${color5}IP Ext: ${color0}${exec wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'}
${endif}${if_existing /proc/net/route ppp0}${voffset 8}${color6}${font StyleBats:size=18}E${font ArtBrush:Bold:size=14}WIRED (ppp0) ${hr 4}
${color5}${upspeedgraph ppp0 20,130 1d273a 6b8fd4} ${downspeedgraph ppp0 20,130 1d273a 6b8fd4}
 ${voffset -23}${color0}${font PizzaDude Bullets:size=15}v${font ArtBrush:size=15}${upspeed ppp0} ${voffset -1}${alignr}${font PizzaDude Bullets:size=15}r${font ArtBrush:size=15}${downspeed ppp0}   
${voffset -2}${font ArtBrush:size=11}${color5}IP local: ${color0}${addr ppp0} ${alignr}${color5}IP Ext: ${color0}${exec wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'} 
${endif}${if_existing /proc/net/route eth1}${voffset 8}${color6}${font Poky:size=18}Y${font ArtBrush:Bold:size=14}WIFI (eth1) ${hr 4}
${color5}${upspeedgraph eth1 20,130 1d273a 6b8fd4} ${downspeedgraph eth1 20,130 1d273a 6b8fd4}
 ${voffset -23}${color0}${font PizzaDude Bullets:size=15}v${font ArtBrush:size=15}${upspeed eth1} ${voffset -1}${alignr}${font PizzaDude Bullets:size=15}r${font ArtBrush:size=15}${downspeed eth1}   
${voffset -6}${font ArtBrush:size=11}${color5}IP: ${color0}${addr eth1} ${alignr}${color5}Antena: ${color0}${wireless_essid eth1} 
${color5}Velocidad: ${color0}${wireless_bitrate eth1} ${alignr}${color5}Mode: ${color0}${wireless_mode eth1} 
${color5}IP Ext: ${color0}${exec wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'} ${color5}${alignr} MAC: ${color0}${wireless_ap eth1} 
${color5}Potencia: ${voffset 2}${wireless_link_bar 8,160 eth1} ${voffset -2}${color0}${alignr}${wireless_link_qual_perc eth1}% ${endif}
```

And the **.conkyrc2B** code:

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 1

# Minimum size of text area
minimum_size 950

# Draw shades?
draw_shades no

# Text stuff
draw_outline no
# amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 0

# border margins
border_margin 0

# border width
border_width 0

# Default colors and also border colors, grey90 == #626262
default_color white
default_shade_color black
default_outline_color grey90

own_window_colour 080d14
own_window_transparent yes
own_window_type override

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 0
gap_y 30

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale yes
xftfont Terminus:size=8
xftalpha 0.8

color0    ffffff    #blanco
color2    6b8fd4    #naranjo

TEXT
${goto 10}${voffset 2}${color0}${font Musicelements:size=18}t${font ArtBrush:Bold:size=14}Rhythmbox - ${if_running rhythmbox} ${exec rhythmbox-client --no-start --print-playing-format %ta} - ${exec rhythmbox-client --print-playing-format %tt} ${hr 2}
${goto 10}${font ArtBrush:size=11} ${color2}Album: ${color0}${exec rhythmbox-client --no-start --print-playing-format %at} ${color2}Genero: ${color0}${exec rhythmbox-client --no-start --print-playing-format %ag} ${color2}Anho: ${color0}${exec rhythmbox-client --no-start --print-playing-format %ay} 
${goto 10}${color2}Posicion: ${color0}${exec rhythmbox-client --no-start --print-playing-format %te} ${color2}Tiempo: ${color0}${exec rhythmbox-client --no-start --print-playing-format %td}${else}${font ArtBrush:size=11:bold}${color2}Sin Actividad${font}${endif}
```

The fonts needed were installed before trying the script.

Thank you very much.

---

### Post by Cavsfan on 2011-01-29
I have mine in **System** > **Preferences** > **Startup Applications** as this:

**conky -c /home/cavsfan/.conkyrc --pause=15**

15 seconds is usually enough time to prevent this issue.

---

### Post by stinkeye on 2011-01-29
Edit your **~/.conky/startconky_b** file to read
```
#!/bin/bash
sleep 20
# Stats Bar
conky -c ~/.conky/.conkyrc1B &
conky -c ~/.conky/.conkyrc2B 

exit
```
Right click on **~/.conky/startconky_b**
Properties > permissions and tick execute.

Then  add to startup applications,using the browse button to link to the location
of your **startconky_b** file.

---

### Post by Mr. ViC on 2011-01-29
> **stinkeye said:**
> Edit your **~/.conky/startconky_b** file to read
```
#!/bin/bash
sleep 20
# Stats Bar
conky -c ~/.conky/.conkyrc1B &
conky -c ~/.conky/.conkyrc2B 

exit
```Right click on **~/.conky/startconky_b**
Properties > permissions and tick execute.

Then  add to startup applications,using the browse button to link to the location
of your **startconky_b** file.

Worked great, thank you :P

By the way, and if it is not asking too much, any idea on how to remove that white border off the conky? :P

Edit: Nevermind, I did it myself.

Thank you again!

---

### Post by stinkeye on 2011-01-29
> **Mr. ViC said:**
> Worked great, thank you :P

By the way, and if it is not asking too much, any idea on how to remove that white border off the conky? :P

Edit: Nevermind, I did it myself.

Thank you again!
Ok good to see you've conkered that one. \\:D/=D>

---

### Post by ajgreeny on 2011-01-31
> **stinkeye said:**
> Ok good to see you've **conkered** that one. \\:D/=D>
Ouch!  I wondered if that old chestnut would appear.

---

### Post by stinkeye on 2011-01-31
> **ajgreeny said:**
> Ouch!  I wondered if that **old chestnut** would appear.


I just wondered is "old chestnut" an old chestnut? ;)

---

### Post by ajgreeny on 2011-01-31
> **stinkeye said:**
> I just wondered is "old chestnut" an old chestnut? ;)
Could be!
[http://en.wikipedia.org/wiki/Conker](http://en.wikipedia.org/wiki/Conker)

---

