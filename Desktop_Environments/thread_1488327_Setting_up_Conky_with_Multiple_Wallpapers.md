---
title: "Setting up Conky with Multiple Wallpapers"
date: 2010-05-19
forum: Desktop Environments
---

### Post by joshbeoulve on 2010-05-19
Hey guys. I have recently installed Lucid Lynx and am enjoying it immensely.
I was just wondering if anyone can help me with setting up Conky to work with the Compiz wallpaper plugin.

I've disabled Nautilus from drawing my desktop to enable multiple wallpapers in Compiz, but now I can't get Conky to show up on the desktop. Can anyone who's done this in Lynx post their .conkyrc files please?

I've tried googling around for a solution, but most of the threads I came across were from 2007-2009, and some of the configuration options for Compiz have been updated since then. It'd be cool if I can still use conky in my multi-paper environment.

Thanks in advance!

Edit:
I'm away from my Ubuntu box by the way, I'll post my .conkyrc contents when I get home.

---

### Post by joshbeoulve on 2010-05-20
Well, I've managed to get it to show on my desktop now, but I can't for the life of me figure out how to get it to become transparent.

Here's my .conkyrc file:

> use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type normal #desktop
own_window_transparent no
own_window_hints undecorated
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers no
uppercase no
color1 F8DF58
double_buffer yes



TEXT
${color 6694B2}${font OpenLogos:size=45} sysname
${color BADCDD}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   ${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    
   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth1} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth1} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth1}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth1}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color F8DF58}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py  3}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}

And here's what my desktop looks like right now:
[IMG]http://i993.photobucket.com/albums/af51/nekokoneko617/Screenshot.gif[/IMG]

---

### Post by bra|10n on 2010-05-20
own_window yes
own_window_type [COLOR=Red]override[/COLOR]
own_window_transparent [COLOR=Red]yes[/COLOR]
own_window_hints undecorated etc etc... - with own_window set to override these settings are ineffectual

---

### Post by joshbeoulve on 2010-05-20
Thanks bra|10n.

I've tried that, and now the conky window won't even show up anymore. This will work if I set Nautilus to draw the desktop, but as I mentioned in my earlier post, I've disabled that (via gconf-editor) so Compiz can take over and I can have different wallpapers on different workspaces.

Any other suggestions? :)

---

### Post by proxess on 2010-05-20
```

own_window yes
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
own_window_type dock
own_window_argb_visual yes
own_window_transparent yes

```

---

### Post by joshbeoulve on 2010-05-20
Nope, no go either. Conky still won't show up. 
I didn't find this line in my original setup
```

own_window_argb_visual yes 
```So I added it up right after own_window_hints.

Here's my .conkyrc so far:
```
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type dock
own_window_transparent yes
own_window_hints undecorated, stick, skip_taskbar, skip_pager, below
own_window_argb_visual yes
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers no
uppercase no
color1 F8DF58
double_buffer yes



TEXT
${color 6694B2}${font OpenLogos:size=45} sysname
${color BADCDD}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   ${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    
   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth1} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth1} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth1}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth1}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color F8DF58}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py josh.beoulve 80057f7400zx!@ 3}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}

```Am I doing anything wrong?

---

### Post by proxess on 2010-05-20
Don't know mate. Wallpaper plugin usually doesn't like Conky all that much.

---

### Post by bra|10n on 2010-05-20
update_interval 1.0

---

### Post by SnickerSnack on 2010-05-30
joshbeoulve, did you ever figure out how to fix this?

I've had a *somewhat* similar problem here: [http://ubuntuforums.org/showthread.php?t=1496860](http://ubuntuforums.org/showthread.php?t=1496860)

---

### Post by stinkeye on 2010-05-30
> **joshbeoulve said:**
> Nope, no go either. Conky still won't show up. 
I didn't find this line in my original setup
```

own_window_argb_visual yes 
```So I added it up right after own_window_hints.

Here's my .conkyrc so far:
```
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type dock
own_window_transparent yes
own_window_hints undecorated, stick, skip_taskbar, skip_pager, below
own_window_argb_visual yes
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers no
uppercase no
color1 F8DF58
double_buffer yes



TEXT
${color 6694B2}${font OpenLogos:size=45} sysname
${color BADCDD}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   ${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    
   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth1} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth1} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth1}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth1}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color F8DF58}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py josh.beoulve 80057f7400zx!@ 3}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}

```Am I doing anything wrong?

This version of your conky will display transparently on my desktops with the
compiz wallpaper plugin.

Make sure that show_desktop is turned off by running in the terminal...
```
gconftool-2 --set /apps/nautilus/preferences/show_desktop --type bool FALSE
```



Conkyrc
```
background yes
update_interval 1.0
total_run_times 0


use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky
own_window_argb_visual yes
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58
double_buffer yes
text_buffer_size 512
override_utf8_locale yes


TEXT
${color 6694B2}${font OpenLogos:size=45} sysname
${color BADCDD}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   ${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    
   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth1} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth1} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth1}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth1}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color F8DF58}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py josh.beoulve 80057f7400zx!@ 3}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}
```

---

### Post by joshbeoulve on 2010-06-02
Omg dude. This looks great! I'll try this out on my Ubuntu box when I get home tonight and report back. Thanks!

---

### Post by thakidd04 on 2012-03-16
bump... I have the same issue as op but im running 11.10 any help? i cant seem to get conky to show with compiz wallpaper enabled. and when i can it shows the wallpaper assigned to nautilus as the background(of conky) if confused i will be happy to clarify... if i can.

my conkyrc

```
background yes
font Bitstream Vera Sans:size=9
xftfont Bitstream Vera Sans:size=9
use_xft yes
xftalpha 0.1
update_interval 1
total_run_times 0

own_window no
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager


double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
minimum_size 300
maximum_width 250
default_color white
default_shade_color 000000
default_outline_color 000000
alignment middle_right
gap_x 2
gap_y 0
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer right
if_up_strictness address

TEXT
$alignc Hostname: $nodename
$alignc Kernel: $kernel
$alignc Uptime: $uptime

${color #B8FF00}CPU:${color white} ${color orange}${freq_g cpu1}${color white}GHz@${color orange}${hwmon 0 temp 1}${color white}°C 
#$alignr GPU: ${color orange}${execi 15 nvidia-settings -query GPUCoreTemp | perl -ne 'print $1 if /GPUCoreTemp.*?: (\d+)./;'} ${color white} °C
${color white}Core0: ${color cyan}${cpubar 8,175} $cpu%
#${color gray}Core1: ${color orange}${cpubar cpu1 8,175} ${color white}${cpu cpu1}%
#${color gray}Core2: ${color red}${cpubar cpu2 8,175} ${color white}${cpu cpu2}%
#${color gray}Core3: ${color #B8FF00}${cpubar cpu3 8,175} ${color white}${cpu cpu3}%
#${color gray}Core4: ${color purple}${cpubar cpu4 8,175} ${color white}${cpu cpu4}%
#${color gray}Core5: ${color orange}${cpubar cpu5 8,175} ${color white}${cpu cpu5}%
#${color gray}Core6: ${color red}${cpubar cpu6 8,175} ${color white}${cpu cpu6}%
#${color gray}Core7: ${color #B8FF00}${cpubar cpu7 8,175} ${color white}${cpu cpu7}%
#${color gray}Core8: ${color purple}${cpubar cpu8 8,175} ${color white}${cpu cpu8}%
${color cyan}${cpugraph 20 97FFFF 528B8B}

${color #B8FF00}Highest CPU:$alignr CPU%  MEM%${color white}
${color #00BFFF}${top name 1}$alignr${top cpu 1}    ${top mem 1}
#${color #32CBFF}${top name 2}$alignr${top cpu 2}    ${top mem 2}
#${color #64D8FF}${top name 3}$alignr${top cpu 3}    ${top mem 3}

${color #B8FF00}MEM:${color white}
RAM ${alignr}$mem / $memmax ($memperc%)
${color purple}${membar 8}
${color white}SWAP ${alignr}$swap / $swapmax ($swapperc%)
${color purple}${swapbar 8}
${memgraph 20 8B008B FF00FF}
${color #B8FF00}Highest MEM: $alignr CPU%   MEM%
${color #D500FF}${top_mem name 1}$alignr${top_mem mem_res 1}     ${top_mem mem 1}
${color #DD32FF}${top_mem name 2}$alignr${top_mem mem_res 2}     ${top_mem mem 2}
${color #E564FF}${top_mem name 3}$alignr${top_mem mem_res 3}     ${top_mem mem 3}

${color #FFFFFF}<- Read/s${alignc -30}HDD${alignr}Write/s ->
${color green}${diskio_read}${color #FF0009}${alignr}${diskio_write}
${color grey}${diskiograph_read 20,150 ff0000 0000ff}${alignr}${color grey}${diskiograph_write 20,150 ff0000 0000ff}${color white}

${color #B8FF00}LAN:${color white} ${alignr}IP: ${addr wlan0}
${color green}LAN Download:                  $alignr${color #FF0009}LAN Upload:
${color green}${downspeedf wlan0} KiB                                  ${alignr}     ${color #FF0009} ${upspeedf wlan0} KiB
${color grey}${downspeedgraph wlan0 20,150 ff0000 0000ff} ${alignr} ${color grey} ${upspeedgraph wlan0 20,150 0000ff ff0000}
${color green}Total:${totaldown wlan0}  ${alignr}${color #FF0009}Total:${totalup wlan0}
```

---

