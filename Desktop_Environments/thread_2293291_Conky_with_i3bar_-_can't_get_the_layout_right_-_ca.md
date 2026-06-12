---
title: "Conky with i3bar - can't get the layout right - can't seem to increase the height"
date: 2015-09-04
forum: Desktop Environments
---

### Post by joel-w-fl on 2015-09-04
Hello.

I just switched from Arch to Ubuntu again, and with the  config that I used for i3 on Arch I get an entirely different result. Or I've copied the wrong config. Anyways. It looks the way I want it, apart from the fact that I can't increase the height of the bar. It's like split in half - see the scrot. The config uses Conky in the I3bar - quite standard. I have tried adding minimum_height - doesn't work. Neither does gap_x, or anything else I've tried. How can I increase the bar's height, so that the text can be read? Help please.

Scrot of the bar in question: [http://i.imgur.com/QOQSbq2.png](http://i.imgur.com/QOQSbq2.png)
My conkyrc: 
```
# Update interval in seconds
update_interval 2.0
own_window_type dock
total_run_times 0
short_units yes
pad_percents 3
override_utf8_locale yes
# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 50
border_inner_margin 50
border_outer_margin 100
minimum_size 250
minimum_height 50
maximum_width 300
mpd
mpd_host 192.168.1.2
mpd_port 1337
#| SF: ${tztime US/Pacific %H:%M} | Free: $memfree | ${exec /home/nick/bin/pacvol.sh display} | $downspeed $upspeed | ${smapi_bat_perc 0}% ${smapi_bat_power 0} | CPU $cpu% [ ${cpu cpu1}.${cpu cpu2}.${cpu cpu3}.${cpu cpu4} ] | ${time %a %d %b | %H:%M} |
TEXT

[
{ "full_text" : "MPD " , "color" : "\#FFFFFF","separator":false } ,
 { "full_text" : " ${if_mpd_playing}${mpd_smart 50} ${mpd_elapsed}/${mpd_length}${else}${mpd_status}${endif} ","separator":false } ,
 { "full_text" :  "HD " , "color" : "\#FFFFFF","separator":false } ,
 { "full_text" : "home: ", "color" : "\#2d2d2d","separator":false } ,
{ "full_text" : "${fs_free /home}/${fs_size /home}","separator":false } ,
{ "full_text" : "root:"  ,"color" : "\#2d2d2d","separator":false } ,
{ "full_text" :  "${fs_free /}/${fs_size /}","separator":false} ,
 { "full_text" : " Ram" , "color" : "\#FFFFFF","separator":false } ,
 { "full_text" : " ${mem}","separator":false},
 { "full_text" : " Wifi " , "color" : "\#FFFFFF","separator":false} ,
 { "full_text" : " ${wireless_essid wlo1}" , "color" : "\#2d2d2d","separator":false } ,
{ "full_text" : " Up: ${upspeed wlo1} Down: ${downspeed wlo1}","separator":false  } ,
 { "full_text" : " Bat" , "color" : "\#FFFFFF","separator":false  } ,
 { "full_text" : " ${battery BAT0} " , "color" :
  ${if_match ${battery_percent BAT0}<20}"\#b95670"${else}"\#404040"${endif} ,"separator":false } ,
 {"full_text": " &#128197; ${time %a %d %b} ", "name":"date"},
 {"full_text": " &#128337; ${time %H:%M} "}
]  ,

```

Relevant parts of i3bar config:
```
bar {
        mode dock
        position bottom

 font xft:anorexia 8
   workspace_buttons yes
   status_command ~/.i3/conky.sh -w 1100 -h 50 -x 333
   colors {
       background       #101010
       statusline       #404040

    # Class colors         border   BACKGR   TEXT   


       focused_workspace  #101010 #1C1D1D #FFFFFF
       active_workspace   #5f5f5f  #101010  #101010
       inactive_workspace #101010  #101010  #2d2d2d
       urgent_workspace   #101010  #999999
        }
}


```

---

