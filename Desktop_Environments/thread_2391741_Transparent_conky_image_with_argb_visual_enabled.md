---
title: "Transparent conky image with argb_visual enabled"
date: 2018-05-12
forum: Desktop Environments
---

### Post by attii87 on 2018-05-12
[FONT=ubuntu]Hi guys! I have a question about Conky. When I enable "own_window_argb_visual" the image becomes transparent and not just the background as it should be. Is there a way to fix it? I'm using Compiz and the latest Ubuntu Mate 18.04. I post my conkyrc below and [here]("https://imgur.com/YFmqQ38") there's the picture which shows the issue. Thank you very much in advance!

[/FONT]```
alignment top_right
background yes
cpu_avg_samples 2
default_color 000000        
default_outline_color 000000     
default_shade_color 000000    
double_buffer yes
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
gap_x 20
gap_y 90
max_specials 1024
max_user_text 10000
maximum_width 100
minimum_size 300 400
net_avg_samples 2
no_buffers yes
override_utf8_locale yes
own_window yes
own_window_colour 000000
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type conky
own_window_argb_visual yes
own_window_argb_value 0
pad_percents 2            
short_units yes            
stippled_borders 3
text_buffer_size 8000
total_run_times 0
update_interval 3.0
uppercase no
use_spacer right
use_xft yes
xftalpha 1


TEXT
${offset 8}${voffset 16}${font OldSansBlack:size=22}${color #232323}${time %H}${offset 12}${time %M}${font}
${font pftempestafivecondensed:size=6}        
        
                 ${color white}Cpu: $cpu%
                 Core:${hwmon 0 temp 1}°C
                 Mem: $mem 
                 Batt: ${battery_percent BAT0}%
                   


                 HOME:${fs_used_perc /home}%
                 ROOT:${fs_used_perc /root}%
                 FREE:${fs_free_perc /home}%
                 Swap:${swapperc}%
   
                 
                CPU:${top cpu 1}%
                ${top name 1}
                MEM:${top_mem mem 1}%
                ${top_mem name 1}                     
                 


                 Signal:                                                                                        
                 ${wireless_link_qual wlp3s0}% 
                 Ul:${upspeed wlp3s0}
                 Dl:${downspeed wlp3s0}
${image ~/.conky/BackPRO.png  115x63 -p -1,204}  
${image ~/.conky/BackDISK.png  115x63 -p -1,138}  
${image ~/.conky/Back.png  115x63 -p -1,6}
${image ~/.conky/BackSYS.png   115x63  -p   -1,72}
${image ~/.conky/BackNET.png  115x63 -p -1,270} 

```

---

### Post by again? on 2018-05-13
I don't think you can fix.
Have to use fake transparency and not "own_window_argb_visual".
See [HERE]("http://conky.pitstop.free.fr/wiki/index.php5?title=ARGB_Visual_(en)") for explanation.

---

### Post by attii87 on 2018-05-16
> **guber2 said:**
> I don't think you can fix.
Have to use fake transparency and not "own_window_argb_visual".
See [HERE]("http://conky.pitstop.free.fr/wiki/index.php5?title=ARGB_Visual_(en)") for explanation.

Thank you, now I know why I have this issue. My best setting should be "own_window_type override" and argb_visual disabled but without it I have the drop shadow (I tried with any & !(class=Conky) in CCSM but it doesn't help). I also tried to change override with others but I don't like the result because the background doesn't become completely transparent. By the way thanks again for your help :)

---

### Post by again? on 2018-05-16
Although the conky man page says...
> **own_window_class**
Manually set the WM_CLASS name. Defaults to "Conky".

xprop shows...
```
WM_CLASS(STRING) = "conky", "conky"
```

In your conky config use...
```
own_window_type **normal**
```

and in ccsm for shadow windows use (note "**conky**" is not capitalised)
```
(any) & !(class=**conky**)
```

---

