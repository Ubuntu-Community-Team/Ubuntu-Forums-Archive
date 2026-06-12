---
title: "Customize Conky"
date: 2011-07-24
forum: Desktop Environments
---

### Post by Frogs Hair on 2011-07-24
Hello ,

I found a simple Conky theme I like and have made some changes . I was able to add CPU % and change the way the memory is displayed .(total memory/used) 

The Conky I started with was made for wireless and I would like to show information for a wired internet .

This is what is currently written in the .conkyrc for wireless 
```
Signal: ${wireless_link_qual wlan0}% 
	Ul: ${upspeed wlan0} kb/s 
	Dl: ${downspeed wlan0} kb/s 
${font}
```

And this is as far as I am on the wired internet and could use some help.
```
${color FFFFFF}${goto 130}${downspeed eth0}
${color FFFFFF}${goto 130}${upspeed eth0}
```

Thanks for any replies !

---

### Post by Frogs Hair on 2011-07-24
This is what it looks like so far.

---

### Post by sectshun8 on 2011-07-24
Am I missing something?  Cuz it seems like you know what to change... are you saying you want that wireless conky to instead display your wired information?  Then what you have would work...

```

    Ul: ${upspeed eth0} kb/s      
    Dl: ${downspeed eth0} kb/s  

${font}
```

---

### Post by Frogs Hair on 2011-07-24
> **sectshun8 said:**
> Am I missing something?  Cuz it seems like you know what to change... are you saying you want that wireless conky to instead display your wired information?  Then what you have would work...

```

    Ul: ${upspeed eth0} kb/s      
    Dl: ${downspeed eth0} kb/s  

${font}
```

I would like display wired internet info and not wireless . I will try the  code above .

---

### Post by Frogs Hair on 2011-07-24
Thank You ! sectshun8

Your code worked just fine .

---

### Post by Frogs Hair on 2011-07-24
Finished for today .```
#!/usr/bin/conky -d -c
##	.conkyrc configuration
alignment bottom_right
background yes
border_margin 5
border_width 5
color0 555555			#
color1 FCAF3E			# zolty
color2 2a2a2a			# braz
color3 a82553			# rozowy f71f84
color4 5e1014			# bordowy
color5 64574e			# braz
color6 2a2a2a			# szary
color7 8888CC			#  (COOL)
color8 9d9c61			# zolto-szary
color9 525276			# niebiesko-szary
cpu_avg_samples 2
default_color 000000		# szary 5f5f5f
default_outline_color 000000 	# Black
default_shade_color 000000	# Black
double_buffer yes
draw_borders no
draw_graph_borders no
draw_outline no
draw_shades no
gap_x 30
gap_y 80
max_specials 1024
max_user_text 10000
maximum_width 200
minimum_size 175
net_avg_samples 2
no_buffers yes
override_utf8_locale yes
own_window override
own_window_colour 000000	# Black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type normal 	## normal
pad_percents 2			# to co nizej, miejsc po przecinku
short_units yes			# krotka wersja podawania wielkosci dyskow np. 612.21M/3.80G
stippled_borders 3
text_buffer_size 8000
total_run_times 0
update_interval 1.0
uppercase no
use_spacer right
use_xft yes
xftalpha 1
xftfont Freesans:pixelsize=9

lua_load /home/didisoft/.conky/lua.lua

# ${diskiograph /dev/sda 15,180 a7a7a7 a7a7a7} # wskaznik pracy dysku
# ${image /home/didisoft/.conky/didisoft.jpg -p 0,80 -s 26x28} # obrazki w conky


TEXT
${font Zegoe Light - U:pixelsize=24}${time %H:%M:%S}${font} 
${font Zegoe Light - U:pixelsize=12}${time %A} - ${time  %B %d, %Y}${font}









${font Zegoe Light - U:pixelsize=24}System${font} 

${offset 0}${font PizzaDude Bullets:pixelsize=12}b${font}		${font Zegoe Light - U:pixelsize=12}Uptime: $uptime_short
       

     Mem: ${offset 9}$color$mem / $memmax${offset 10}
     ${color 111000}CPU ${offset 9}$color${cpu cpu0}%
     Storage: ${fs_used /} / 40G



        

       Signal-Eth0  
       Ul: ${upspeed eth0} kb/s      
       Dl: ${downspeed eth0} kb/s   
${font}



${font Zegoe Light - U:pixelsize=24}To Do${font}

${offset 0}${font PizzaDude Bullets:pixelsize=12}b${font}	${font Zegoe Light - U:pixelsize=12} - Enjoy The Weekend
${font}	  	

```

---

