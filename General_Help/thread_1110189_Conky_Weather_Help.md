---
title: "Conky Weather Help"
date: 2009-03-29
forum: General Help
---

### Post by ninjapirate89 on 2009-03-29
I am getting really frustrated. I tried following this
[http://ubuntuforums.org/showthread.php?t=869328]("http://ubuntuforums.org/showthread.php?t=869328")
but I can't get it to work . Can someone give me a very simple step-by-step on how to do this? I only made it through installation and setting up a weather.com account.

---

### Post by ninjapirate89 on 2009-03-29
bump

---

### Post by VCoolio on 2009-03-29
1. install conkyForecast
2. in your home folder should be a hidden file named .conkyForecast.config. Open it in gedit and paste your xoap id and key you received by email.
3. in your home folder or in .scripts in your homefolder or in usr/share/conkyforecast should be a file named conkyForecast.py. I copied it elsewhere so I'm not sure about the default location (run "locate conkyForecast.py" if you can't find it). Open it in gedit and enter your location code where it says $location (for me that was in line 68 ). Search for the code of your location in weather.com.
4. Save conkyForecast.py where you want it (you may not want to have all kind of crap in your home folder).
5. Paste the appropriate command in your conky config file. You can get examples from /usr/share/conkyforecast/example. For me this works for a three-day-forecast (you must change the location code of course and use the accurate location of your .py script):```

${font Weather:size=32}${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0018 --datatype=WF}${font Verdana:size=8}${color3}${voffset -24} ${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0018 --datatype=HT}   ${font Weather:size=32}${color}${voffset}${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0018 --datatype=WF --startday=1}${font Verdana:size=8}${color3}${voffset -24} ${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0018 --datatype=HT --startday=1}   ${font Weather:size=32}${color}${voffset}${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0018 --datatype=WF --startday=2}${font Verdana:size=8}${color3}${voffset -24} ${execi 3600 python ~/.scripts/conkyForecast.py --location=NLXX0018 --datatype=HT --startday=2}
```
That's what I can remember of it. Hope it works.

---

### Post by ninjapirate89 on 2009-03-29
Thank you VCoolio. It seems to be working now. Now I just need to incorporate this into my original conkyrc file and I'll be all set. The part I was missing was the partner ID and the License Key. I didn't know it sent me an email with that info. I was just trying the username and password for the weather.com account. Thanks again.

---

### Post by ben2talk on 2009-04-08
# config settings for conkyForecast.py
CACHE_FOLDERPATH = /tmp/
CONNECTION_TIMEOUT = 5
EXPIRY_MINUTES = 30
TIME_FORMAT = %H:%M
DATE_FORMAT = %Y-%m-%d
LOCALE = THXX0002
XOAP_PARTNER_ID = xxxxxxxxxx
XOAP_LICENCE_KEY = xxxxxxxxxx

What format for locale? is this the code 'THXX0002' (for Bangkok)?

Anyone having problems with 'XOAP' - have to register for XML web feed, and click to skip lots of advertisements.

Update - that was the toughest part (internet here sucks)

Conky's perfect now - just messin around editing the template to fit my smaller conky.

Great fun!

---

### Post by devildoc5 on 2010-03-17
I know this thread is old and dead but hopefully someone out there will have the answer for me...I followed all steps...except for I cannot locate conkyForecast.config or .py  I try and install it though and apt yells at me and says latest version is already installed...Anyone able to help?

---

### Post by nontee on 2010-05-05
_this is my script_

# conky configuration
background yes
update_interval 1.0

own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
own_window_type normal
double_buffer yes

draw_shades no

draw_outline no

draw_borders no

draw_graph_borders yes

stippled_borders 0

border_margin 10

border_width 2

default_color white
default_shade_color black
default_outline_color black

minimum_size 5 5
maximum_width 256

alignment top_right

gap_x 5
gap_y 1

text_buffer_size 1000

no_buffers yes

uppercase no

cpu_avg_samples 1

net_avg_samples 1


use_spacer right

use_xft yes


TEXT
${font :size=7}${alignc}${color yellow}$sysname $kernel ${pre_exec id -un} @ ${nodename}
${color }CPU TEMP:${color D7D3C5}${acpitemp}°c ${alignr} ATi VGA TEMP  ${execi 60 aticonfig --adapter=0 --od-gettemperature}°C
${voffset -5}${alignc 65}${color lightyellow}${font :size=30}${time %H:%M:%S}$font$color
${voffset -2}${alignc}${font angsima bolt:size=12}${time &#3623;&#3633;&#3609;%A&#3607;&#3637;&#3656; %d, %B. %G}$font
${voffset -10}${font :size=7}${voffset -5}${color #888888}${hr 1}$color$voffset
${font :size=7}${voffset -5}${freq cpu0} MHz${alignc -35}$loadavg
${voffset -2}${alignr 50}${cpugraph 28,180 000000 ff0000}$voffset${voffset -5}${color red}${font :size=20}${alignr}${cpu cpu0}%$font$color
${voffset -12}${font :size=7}${voffset -22}Uptime:${alignr}$uptime$color
${voffset -7}${color #888888}${hr 1}$color
${color green}${alignr}${membar 11,120}$color
${voffset -19}$memperc%  RAM used: $mem${alignr}${offset 10}${color #888888}/$color$memmax$offset$voffset
${color green}${alignr}${swapbar 11,120}$color
${voffset -19}$swapperc% Swap used: $swap${alignr}${offset 10}${color #888888}/$color$swapmax$offset$voffset
Cache used: $cached
${voffset -8}${color #888888}${hr 1}$color
${color #888888}Processes: $color$processes                    ${color #888888}Running: $color$running_processes$offset
${voffset -5}${color #888888}${hr 1}$color
${voffset -5}${color green}      NAME                        PID         CPU%        MEM%  $color
${voffset -5}${top name 1}              ${top pid 1}        ${top cpu 1}           ${alignr 25}${top mem 1}
${voffset -5}${top name 2}              ${top pid 2}        ${top cpu 2}           ${alignr 25}${top mem 2}       
${voffset -5}${top name 3}              ${top pid 3}        ${top cpu 3}           ${alignr 25}${top mem 3}
${voffset -5}${top name 4}              ${top pid 4}        ${top cpu 4}           ${alignr 25}${top mem 4}
${voffset -5}${top name 5}              ${top pid 5}        ${top cpu 5}           ${alignr 25}${top mem 5}
${voffset -5}${color #888888}${hr 1}
${voffset -5}${color green}Root: $color${fs_free /}${color #888888}${font :size=7} Is Free for Contain the Files$font${alignr}${color red}${diskio /dev/sda5}$color$voffset
${voffset -12}       ${color #333333}${fs_bar 11,208 /}$color${offset -205}${font :size=7}${fs_used /}$font$offset
${alignc}${color purple}${voffset 10}${execi 60 hddtemp /dev/sda1 | cut -c32-36;}$offset$color
${font :size=7}${voffset -60}${color green}Home: $color${fs_free /home}${color #888888}${font :size=7} Is Free for Contain the Files$font${alignr}${color red}${diskio /dev/sda7}$color
${voffset -12}       ${font :size=7}${voffset -3}${color #333333}${fs_bar 11,208 /home}$color${offset -205}${font :size=7}${fs_used /home}$font$offset
${voffset -22}${color #888888}${hr 0}$color
 ${voffset -10}${font :size=8}${color lightblue}Uploading:   ${alignr 8}${color green}Downloading:$color$font
 ${voffset -8}${font :size=10}${upspeedf eth0}KB/s     ${alignr 20}${downspeedf eth0}KB/s$font
 ${voffset -3}${color lightblue}${upspeedgraph eth0 25,104 000000 ff0000} ${alignr}${downspeedgraph eth0 25,104 000000 00ff00}$color
${voffset -5}${font :size=7}&#3629;&#3633;&#3614;&#3650;&#3627;&#3621;&#3604;&#3607;&#3633;&#3657;&#3591;&#3626;&#3636;&#3657;&#3609; = ${totalup eth0} ${alignr}&#3604;&#3634;&#3623;&#3609;&#3660;&#3650;&#3627;&#3621;&#3604;&#3607;&#3633;&#3657;&#3591;&#3626;&#3636;&#3657;&#3609; = ${totaldown eth0}
${voffset -10}${color #888888}$hr$color
${voffset -5}${color lightgreen}${font :size=9}     &#3614;&#3618;&#3634;&#3585;&#3619;&#3603;&#3660;&#3629;&#3634;&#3585;&#3634;&#3624;&#3651;&#3609;&#3648;&#3586;&#3605;&#3585;&#3619;&#3640;&#3591;&#3648;&#3607;&#3614;&#3617;&#3627;&#3634;&#3609;&#3588;&#3619;$font$color
${voffset -22}${color #888888}$hr$color 
     ${if_existing /proc/net/route wlan0}
     ${else}${if_existing /proc/net/route eth0}
${voffset -45}${font tahoma:size=7}${color}&#3607;&#3657;&#3629;&#3591;&#3615;&#3657;&#3634;&#3648;&#3627;&#3609;&#3639;&#3629;&#3585;&#3619;&#3640;&#3591;&#3648;&#3607;&#3614;&#3631;&#3651;&#3609;&#3586;&#3603;&#3632;&#3609;&#3637;&#3657;: ${color yellow}${font tahoma:size=7}${execi 600 conkyForecast --location=THXX0022 --datatype=CC}${font}$color
     ${voffset -15}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=THXX0022 --datatype=WF}${font}
${voffset -48}${color green}${font tahoma:size=18}&#3629;&#3640;&#3603;&#3627;&#3616;&#3641;&#3617;&#3636;: ${font Weather:size=40}${font} ${voffset -55}${color lightgreen}${font tahoma:size=24}${execi 600 conkyForecast --location=THXX0022 --datatype=HT}${font}$color

${voffset -22}${font ConkyWeather:size=29} ${color lightblue}${execpi 600 conkyForecast --location=THXX0022 --datatype=WF --startday=1 --endday=5 --spaces=1}${font}$color
${font :size=7}${color green}${voffset -19}${alignc 60}${execpi 600 conkyForecast --location=THXX0022 --datatype=DW --startday=1 --shortweekday} ${alignc 20}${execpi 600 conkyForecast --location=THXX0022 --datatype=DW --startday=2 --shortweekday} ${alignc -15}${execpi 600 conkyForecast --location=THXX0022 --datatype=DW --startday=3 --shortweekday} ${alignc -54}${execpi 600 conkyForecast --location=THXX0022 --datatype=DW --startday=4 --shortweekday} ${alignc -95}${execpi 600 conkyForecast --location=THXX0022 --datatype=DW --startday=5 --shortweekday}$color
${voffset -7}${font DejaVu Sans:size=7}${alignc 20}${execpi 600 conkyForecast --location=THXX0022 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=THXX0022 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -10}${execpi 600 conkyForecast --location=THXX0022 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=THXX0022 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=THXX0022 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=THXX0022 --datatype=LT --startday=3 --hideunits --centeredwidth=3}  ${alignr 22}${execpi 600 conkyForecast --location=THXX0022 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=THXX0022 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font DejaVu Sans:size=7}${alignr 12}${execpi 600 conkyForecast --location=THXX0022 --datatype=HT --startday=5 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=THXX0022 --datatype=LT --startday=5 --hideunits --centeredwidth=3}${font}$color
${voffset -28}${font DejaVu Sans:size=7}${alignc 30}${execpi 600 conkyForecast --location=THXX0022 --datatype=WS --startday=1 --hideunits --centeredwidth=3} Kph${alignc}${execpi 600 conkyForecast --location=THXX0022 --datatype=WS --startday=2 --hideunits --centeredwidth=3} Kph${alignc -32}${execpi 600 conkyForecast --location=THXX0022 --datatype=WS --startday=3 --hideunits --centeredwidth=3} Kph${alignr 27}${execpi 600 conkyForecast --location=THXX0022 --datatype=WS --startday=4 --hideunits --centeredwidth=3} KpH${alignr 17}${execpi 600 conkyForecast --location=THXX0022 --datatype=WS --startday=5 --hideunits --centeredwidth=3} Kph

#${voffset -10}${font MoonPhases:size=9}${color yellow}${alignc 30}${execpi 600 conkyForecast --location=THXX0022 --datatype=MP --startday=1 --hideunits --centeredwidth=3}${alignc}${execpi 600 conkyForecast --location=THXX0022 --datatype=MP --startday=2 --hideunits --centeredwidth=3}${alignc -32}${execpi 600 conkyForecast --location=THXX0022 --datatype=MP --startday=3 --hideunits --centeredwidth=3}${alignr 27}${execpi 600 conkyForecast --location=THXX0022 --datatype=MP --startday=4 --hideunits --centeredwidth=3}${alignr 17}${execpi 600 conkyForecast --location=THXX0022 --datatype=MP --startday=5 --hideunits --centeredwidth=3}

${alignr 140}${voffset -28}${font :size=7}$color&#3604;&#3623;&#3591;&#3629;&#3634;&#3607;&#3636;&#3605;&#3618;&#3660;&#3586;&#3638;&#3657;&#3609;&#3648;&#3623;&#3621;&#3634;: ${color yellow}${execi 600 conkyForecast --location=THXX0022 --datatype=SR}${font tahoma:size=7}$color &#3609;.&#3604;&#3623;&#3591;&#3629;&#3634;&#3607;&#3636;&#3605;&#3618;&#3660;&#3605;&#3585;&#3648;&#3623;&#3621;&#3634;: ${color yellow}${execi 600 conkyForecast --location=THXX0022 --datatype=SS}${font :size=7} &#3609;.$color
${voffset -6}${font :size=7}&#3588;&#3623;&#3634;&#3617;&#3594;&#3639;&#3657;&#3609;&#3626;&#3633;&#3617;&#3614;&#3633;&#3607;&#3651;&#3609;&#3629;&#3634;&#3585;&#3634;&#3624;:------------------------- ${color yellow}${alignc -45}${execi 600 conkyForecast --location=THXX0022 --datatype=HM}$color 
${voffset -6}${font :size=7}&#3588;&#3623;&#3634;&#3617;&#3648;&#3619;&#3655;&#3623;&#3621;&#3617;&#3648;&#3593;&#3621;&#3637;&#3656;&#3618;:----------------------------- ${color yellow}${alignc -45}${execi 600 conkyForecast --location=THXX0022 --datatype=WS}$color
${voffset -21}${alignc -85}${color yellow}${font MoonPhases:size=30}${execi 600 conkyForecast --location=THXX0022 --datatype=MF}${font}$color
${alignr 50}${voffset -39}${font tahoma:size=7}&#3626;&#3606;&#3634;&#3609;&#3607;&#3637;&#3656;: ${color yellow}${execi 600 conkyForecast --location=THXX0022 --datatype=OB}$color
${voffset -5}${font tahoma:size=7}&#3607;&#3633;&#3624;&#3609;&#3632;&#3623;&#3636;&#3626;&#3633;&#3618;&#3651;&#3609;&#3585;&#3634;&#3619;&#3617;&#3629;&#3591;&#3648;&#3627;&#3655;&#3609;: ${color yellow}${execi 600 conkyForecast --location=THXX0022 --datatype=VI} ${font tahoma:size=7}$color &#3607;&#3636;&#3624;&#3607;&#3634;&#3591;&#3621;&#3617;: ${color yellow}${execi 600 conkyForecast --location=THXX0022 --datatype=WD}
${voffset -5}${color lightblue}${font :size=7}&#3621;&#3633;&#3585;&#3625;&#3603;&#3632;&#3586;&#3629;&#3591;&#3604;&#3623;&#3591;&#3592;&#3633;&#3609;&#3607;&#3619;&#3660;&#3651;&#3609;&#3588;&#3639;&#3609;&#3609;&#3637;&#3657;: ${voffset 0}${color yellow}${execi 600 conkyForecast --location=UKXX0176 --datatype=MP} Moon$color${font}$color      
${voffset -20}${font tahoma:size=7}&#3611;&#3619;&#3633;&#3610;&#3611;&#3619;&#3640;&#3591;&#3586;&#3657;&#3629;&#3617;&#3641;&#3621;&#3629;&#3634;&#3585;&#3634;&#3624;&#3621;&#3656;&#3634;&#3626;&#3640;&#3604;&#3648;&#3617;&#3639;&#3656;&#3629;: ${color yellow}${execi 600 conkyForecast --location=THXX0022 --datatype=LF}
${endif}
${voffset -25}${color #888888}$hr$color
${voffset -6}${font :size=9}${alignc}${color}&#3648;&#3614;&#3621;&#3591;&#3607;&#3637;&#3656;&#3585;&#3635;&#3621;&#3633;&#3591;&#3648;&#3621;&#3656;&#3609;&#3651;&#3609; RhythmBox Music Player:
${voffset -4}${font :size=8}${color lightgreen}&#3594;&#3639;&#3656;&#3629;&#3648;&#3614;&#3621;&#3591;: ${color lightblue}${voffset -2}${font tahoma:size=11}${execi 10 rhythmbox-client --no-start --print-playing-format %tt}
${voffset -8}${font :size=8}${color lightgreen}&#3594;&#3639;&#3656;&#3629;&#3624;&#3636;&#3621;&#3611;&#3636;&#3609;: ${color lightblue}${font :size=8}${execi 10 rhythmbox-client --no-start --print-playing-format %aa} 
${voffset -2}${font :size=8}${color lightgreen}&#3594;&#3639;&#3656;&#3629;&#3629;&#3633;&#3621;&#3610;&#3633;&#3657;&#3617;: ${font :size=8}${color lightblue}${execi 10 rhythmbox-client --no-start --print-playing-format %at}

---

