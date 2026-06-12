---
title: "conky alignment"
date: 2009-01-11
forum: General Help
---

### Post by anunez on 2009-01-11
im trying to split my conky into 2 areas of the screen. i have it currently set at top left and i would like to move only the the calender to the top right. i tried adding that to conkyrc but could not figure out how to get that to work, any help would be appreciated

---

### Post by kerry_s on 2009-01-11
posting your conkyrc could help. you know you can run more than 1 conky instance. "man conky" in terminal

---

### Post by anunez on 2009-01-11
here is my conkyrc. also i tried to run two instances of conky but couldent get that to work.



conky


# set to yes if you want Conky to be forked in the background
    background yes
    use_xft yes
    xftfont HandelGotD:size=7
    xftalpha 0.5
    update_interval 4.0
    total_run_times 0
    own_window yes
    own_window_type normal
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    double_buffer yes
    minimum_size 200 5
    maximum_width 200
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders yes
   
    default_color white
    default_shade_color red
    default_outline_color grey
    alignment top_right
    #alignment top_left

    gap_x 12
    gap_y 48
    no_buffers yes
    uppercase no
    cpu_avg_samples 2
    override_utf8_locale yes

    

    TEXT 
    ${font Arial:bold:size=10}${color Tan1}University of the Pacific ${hr 2}${color}
    ${alignc 18}${font Arial Black:size=12}Andres Nunez, MA${font}
    ${alignc -14}${color Tan1}School Psychology ${color}
    DATE ${hr 2}
    ${alignc 35}${font Trebuchet MS:size=26}${time %I:%M}${font}
    ${alignc}${time %a %d %b %Y}

    System ${hr 2}
    ${font StyleBats:size=16}A${font}    CPU1: ${cpu cpu1}% ${alignr}${color 228B22}${cpubar cpu1 8,60}${color}
    ${font StyleBats:size=19}g${font}   RAM: $memperc% ${alignr}${color ff0000}${membar 8,60}${color}
    ${font StyleBats:size=19}j${font}   SWAP: $swapperc% ${alignr}${color f17f17}${swapbar 8,60}${color}
   ${font Webdings:size=19}~${font}   Battery: ${battery_percent BAT0}% ${color 1874CD}${alignr}${battery_bar 8,60 BAT0}${color}
    ${font StyleBats:size=19}q${font}   Uptime: ${alignr}${uptime}
   
    
    Root $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
    ${color ff0000}${fs_bar /}${color}}
    
    Processes ${hr 2}
    $processes processes ($running_processes running)
    Load Average${alignr}$loadavg
    NAME $alignr PID   CPU   MEM
    ${top name 1} $alignr ${top pid 1} ${top cpu 1} ${top mem 1}
    ${top name 2} $alignr ${top pid 2} ${top cpu 2} ${top mem 2}
    ${top name 3} $alignr ${top pid 3} ${top cpu 3} ${top mem 3}
    ${top name 4} $alignr ${top pid 4} ${top cpu 4} ${top mem 4}
    ${top name 5} $alignr ${top pid 5} ${top cpu 5} ${top mem 5}

    WEATHER ${hr 2}
    ${if_existing /proc/net/route eth0}
    ${voffset -8}${font ConkyWeather:size=36}${execi 500 /usr/bin/conkyForecast --location=USCA1100 --datatype=WF}${font}
    ${voffset -52}${font ConkyWeather:size=40}          ${font}${voffset -40}${font sans:size=26}${execi 500 /usr/bin/conkyForecast --location=USCA1100 --datatype=HT --imperial}${font}    
    ${voffset 0}${font}Barometer Tendency: ${alignr}${execi 500 /usr/bin/conkyForecast --location=USCA1100 --datatype=BD}
    ${voffset 0}Humidity: ${alignr}${execi 500 /usr/bin/conkyForecast --location=USCA1100 --datatype=HM}
    ${voffset 0}${font}Wind Speed: ${alignr}${execi 500 /usr/bin/conkyForecast --location=USCA1100 --hideunits --datatype=WS} mph ${execi 500 /usr/bin/conkyForecast --location=USCA1100 --hideunits --datatype=WD}
    ${voffset 0}Daylight: ${alignr}${execi 500 /usr/bin/conkyForecast --location=USCA1100 --datatype=SR} - ${execi 500 /usr/bin/conkyForecast --location=USCA1100 --datatype=SS}
    ${voffset 0}Moon Phase:   
    ${font Trebuchet MS:size=12}${execi 600 /usr/bin/conkyForecast --location=USCA1100 --datatype=MP}
    ${voffset -30}${alignr 42}${font MoonPhases:size=28}${execi 600 /usr/bin/conkyForecast --location=USCA1100 --datatype=MF}${font}
    Keyboard Shortcuts ${hr 2}
    Alt+F2$alignr Run Dialog
    Alt+F3$alignr Alt Menu
    Super+space$alignr Main Menu
    Super+t$alignr Terminal
    Super+f$alignr File Manager
    Super+e$alignr Editor
    Super+m$alignr Media Player
    Super+w$alignr Web Browser
    Super+g$alignr Graphics Editor
    Super+l$alignr Lock Screen
    Super+v$alignr Volume Control
    Super+x$alignr Logout
    PrtSc$alignr Screenshot

---

### Post by kerry_s on 2009-01-11
> here is my conkyrc. also i tried to run two instances of conky but couldent get that to work.

to run several instances you create the several conkyrc files:

to run the conky you got now:
conky -cd ~/.conkyrc

then create a new conyrc, thats call it conkyrc2:
conky -cd ~/.conkyrc2

and so on. you can name it what ever you want, it's up to you:
conky -cd ~/.calendar

i'm not running conky so i'm going to leave you to someone who can try your script and maybe suggest a fix. good luck

just had a thought the command might be:
conky -d -c ~/.conkyrc

it's been a while. -d runs it as a daemon.

---

### Post by Wartender on 2009-01-11
well try adding ${alignr} before the call for the calendar.

---

### Post by kerry_s on 2009-01-11
i was thinking that to but he's trying to span the whole desktop wouldn't:

```
minimum_size 200 5
maximum_width 200
```

prevent it exceeding that size?

---

### Post by Wartender on 2009-01-11
yes that's true you also have to increas the size to match the resolution of your desktop (minus panels, which conky cannot be on top of), you should do this along with the ${alignr}

---

### Post by anunez on 2009-01-12
ok awesome so running the 2nd conky gave me the effect i wanted. but i have one more question how do i get both instances of conky to run at start up. what i been doing is once started i run the 2nd conkyrc

---

### Post by kerry_s on 2009-01-12
> **anunez said:**
> ok awesome so running the 2nd conky gave me the effect i wanted. but i have one more question how do i get both instances of conky to run at start up. what i been doing is once started i run the 2nd conkyrc

same way you start the first:
i assume for the first you have:
conky -d &
so for the second:
conky -d -c ~/.conky2 &

---

### Post by fractalz on 2009-03-04
> **kerry_s said:**
> same way you start the first:
i assume for the first you have:
conky -d &
so for the second:
conky -d -c ~/.conky2 &

Effectively you could write the following shell script like conky.sh and call it at startup:

```

#! /bin/bash

(sleep 2s && conky -d) &
(sleep 2s && conky -d -c ~/.conky2) &


```

Even better move all conkyrc files to a hidden directory like ~/.conky
and give them names like: .conky_sys , .conky_net etc. depending on what they show and modify the shell script above:

```

#! /bin/bash

(sleep 2s && conky -d -c ~/.conky/.conky_sys) &
(sleep 2s && conky -d -c ~/.conky/.conky_net) &


```

I've added sleep to the script but it is not really necessary if the scripts are tiny, though I like to add them anyway. You could also add sleep in the startup script instead like:

```

(sleep 3s && ~/.conky/.conky.sh)

```

---

