---
title: "Conky in Cinnamon"
date: 2012-03-01
forum: Desktop Environments
---

### Post by EdTheUniqueGeek on 2012-03-01
Anyone running custom Conky themes in the Cinnamon environment successfully?
I'm having problems.

---

### Post by stinkeye on 2012-03-01
My conkys will run but ignore the position settings
and just open in top left. Cairo-clock does the same.
Must have something to do with the window manager for cinnamon.
**wmctrl -m** tells me it's "Muffin".

---

### Post by goinglinux on 2012-03-01
I got around this by using this in the conky.rc file:

```
alignment top_left
gap_x 1120
gap_y 10
```

Adjust the horizontal and vertical gap from the top left until things are at the right place on the screen

---

### Post by EdTheUniqueGeek on 2012-03-01
Well the reason I ask is because of a custom theme I could run in Gnome I cannot now in Cinnamon.
Sorry to post a thread from a different forum, but this is the thorough run down:
[http://forums.linuxmint.com/viewtopic.php?f=212&t=95769](http://forums.linuxmint.com/viewtopic.php?f=212&t=95769)

Here is the short story:
After I installed Conky I created the directory ~/.conkyrc and placed the files from the Conky Orange (and even tried Conky Lunatico Rings) in that folder. When I ran *conky* from the terminal, I get this error:

```
Conky: invalid configuration file '/home/ed/.conkyrc'

Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
   This program is calling the Imlib call:

   imlib_context_free();

   With the parameter:

   context

   being NULL. Please fix your program.

```

And what is interesting is that I have the TEXT block in the config file.

---

### Post by stinkeye on 2012-03-01
> **goinglinux said:**
> I got around this by using this in the conky.rc file:

```
alignment top_left
gap_x 1120
gap_y 10
```

Adjust the horizontal and vertical gap from the top left until things are at the right place on the screen

Tried 
```
alignment top_left
gap_x 600
gap_y 50
```
Still opens in top left.

---

### Post by stinkeye on 2012-03-01
**@ EdTheUniqueGeek**
one thing I did notice was if I used
```
own_window_type **override**
```
conky failed to appear.



Whereas 
```
own_window_type **normal**
own_window_hints undecorated,below,skip_taskbar,skip_pager,sticky
```
conky was shown but loaded in the topleft.

I run 4 conkys and they were loading on top of each other.

I don't use Cinnamon, I had it installed so I
was just doing a bit of testing to see if I could help.
Try here for an answer [**_[COLOR="DarkRed"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865")

P.S to make sure your running the right config try
starting your conky with 
```
conky -c */path/to/config*
```
Also did you install the **conky-all** package which is compiled to use lua.
The normal conky wont work with lua.

**PPS:** I downloaded **Conky Lunatico Rings** and in runs here on Ubuntu 11.10
with cinnamon as the desktop session.
Just had to use ```
own_window_type **normal**
```

---

### Post by EdTheUniqueGeek on 2012-03-01
Thanks, stinkeye, for all the suggestions.
I tried everyone and still I get the output:

```
ed@ed-xps-mint12 ~ $ conky -c ~/.conkyrc
Conky: invalid configuration file '/home/ed/.conkyrc'

Conky: invalid configuration file '/home/ed/.conkyrc'

Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.

```

I don't get it.

---

### Post by stinkeye on 2012-03-01
What happens running
```
conky -c ~/.conky/conkyrc_lunatico
```


The **~/.conky** folder should contain 
**conky_lunatico.lua** and **conkyrc_lunatico**

and the line in your **conkyrc_lunatico** for lua should have the correct path
eg```
lua_load ~/.conky/conky_lunatico.lua
```

---

### Post by EdTheUniqueGeek on 2012-03-02
Wow. I'm a ditz. I wasn't putting the full path at the terminal.
I put in *conky -c ~/.conkyrc/conkyrc_lunatico* and it works just fine now.
Thanks a million.

---

### Post by stinkeye on 2012-03-02
> **EdTheUniqueGeek said:**
> Wow. I'm a ditz. I wasn't putting the full path at the terminal.
I put in *conky -c ~/.conkyrc/conkyrc_lunatico* and it works just fine now.
Thanks a million.
Yeah had a feeling it was something like that.
It's like when you loose something and search in ever increasing circles
and then find it back where you started.
#-o

---

### Post by EdTheUniqueGeek on 2012-03-02
Yep, exactly.
Also, ultimately, changing that line from **override** to **normal** was the real fix. For the hell of it I change it back to **override** to see what would happen and it did not work. Changed it back to **normal** and it worked.
Good catch. Thanks again.

---

### Post by NikTh on 2012-06-01
> **EdTheUniqueGeek said:**
> Yep, exactly.
Also, ultimately, changing that line from **override** to **normal** was the real fix. For the hell of it I change it back to **override** to see what would happen and it did not work. Changed it back to **normal** and it worked.
Good catch. Thanks again.
+1 Yeap , 
this is the fix.** From override to normal** . 
This fixed my invisible conky. 
Thanks .

---

### Post by dentex on 2012-11-29
Hi everyone.
The fix works OK, but when I click the "show desktop button" conky disapperas.
now: when I click again it comes back with all other windows, but if I click something else AND THEN "show desktop", conky stays hidden...

just my 2cents.

---

### Post by stinkeye on 2012-11-29
> **dentex said:**
> Hi everyone.
The fix works OK, but when I click the "show desktop button" conky disapperas.
now: when I click again it comes back with all other windows, but if I click something else AND THEN "show desktop", conky stays hidden...

just my 2cents.

Don't know with Cinnamon but with compiz I need to unmark 
**Hide Skip Taskbar Windows** in ccsm.

---

### Post by boudiccas on 2013-07-05
[I]I will return tomorrow and hopefully post some correct output.

Sharon.[/I]

---

### Post by boudiccas on 2013-07-05
##################################
## boudiccas | rev. 05-07-13 ##
##################################
# conky -dc ~/.conky/.conkyrc10
# from .bash_aliases where the complete line is 'alias conky='nohup conky -dc ~/.conky/.conkyrc10 &''


background no
    font DroidSans:size=8
    #xftfont sans:size=10
    use_xft yes
    xftalpha 0.9
    update_interval 1.0
    total_run_times 0
    own_window yes
    own_window_transparent yes
    own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
    own_window_type normal
    double_buffer yes
    minimum_size 200
    maximum_width 225
    draw_shades no
    draw_outline no
    draw_borders no
    draw_graph_borders yes
    default_color white
    default_shade_color black
    default_outline_color green
    alignment top_right
    gap_x 15
    gap_y 15
    no_buffers yes
    uppercase no
    cpu_avg_samples 2
    override_utf8_locale no
    uppercase no


    # Define some Colors
    color0 tan2      # Headings
    color1 slategrey   # Horizonal lines
    color2 Ivory2      # Text
    


TEXT
##################################
##             LOGO             ##
##################################
## Uncomment for hard-coded ID (static)
#${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}1${offset 1}2${offset 1}.${offset 0}0${offset 0}4${font}
####
## Uncomment for soft-coded ID (dynamic)
# ${voffset -33}${font #OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font UbuntuTitleBold:size=19.6}${color4}${pre_exec cat /etc/*release | grep 'RELEASE' | awk -F'=' '{print $2}'}${font}
####
## Additional ID (branch version, code name, release date, etc.)
#${voffset -1}${goto 188}${font Ubuntu-B:size=8.1}${color4}alpha 1${font}
##################################
##            SYSTEM            ##
##################################
#${voffset 7}${font DroidSans:bold:size=8.25}${color4}SYSTEM${offset 8}${color8}${voffset -2}${hr 2}${font}
#${voffset 4}${font OpenLogos:size=10}${color2}u${voffset -4}${font DroidSans:size=8.6}${color3}${offset 5}${pre_exec lsb_release -sd || cat /etc/*release}${font}
#${voffset 2}${offset -2}${font OpenLogos:size=12}${color2}Z${voffset -4}${font DroidSans:size=8.6}${color3}${offset 3}${sysname}${offset 3}${kernel}${alignr}${font DroidSans:size=8.3}${machine}${font}
#${voffset 2}${font StyleBats:size=10}${color2}d${voffset -2}${font DroidSans:size=8.6}${color3}${offset 5}nVidia GeForce 7600 GT${alignr}${font DroidSans:size=8.3}#${pre_exec dpkg --status nvidia-current | grep Version | cut -f 1 -d '-' | sed 's/[^.,0-9]//g'}${font}
#${voffset 2}${font StyleBats:size=10}${color2}A${voffset -1}${font DroidSans:size=8.6}${color3}${offset 5}Intel${offset 3}P4${offset 3}Extreme${offset 3}Edition${alignr 1}${font DroidSans:size=8.3}${freq_g cpu0}${offset 1}GHz${font}
#${voffset 7}${alignr} CPU freq: ${freq_g cpu0}${offset 1}GHz${font}
${voffset 2}${font StyleBats:size=10}${color2}q${voffset -1}${font DroidSans:size=8.6}${color3}${offset 5}System${offset 3}Uptime${alignr}${font DroidSans:size=8.3}${uptime}${font}
##################################
##          PROCESSORS          ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}PROCESSORS${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU1${offset 5}${font DroidSans:size=8.3}${cpu cpu1}${font} ${voffset 2}${alignc}${font StyleBats:size=9.9}${color2}k${voffset -2}${font DroidSansFallback:size=8.39}${color3}${offset 2}CPU2${offset 5}${font DroidSans:size=8.3}${cpu cpu2}%${font}
##################################
##            MEMORY            ###
##################################
${voffset 5}${font DroidSans:bold:size=8}${color4}MEMORY${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font StyleBats:size=10}${color2}l${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 3}RAM${goto 97}${font DroidSans:size=8.3}${mem}${goto 133}/${offset 5}${memmax}${alignr}${memperc}%${font}
################################## /media/boudiccas/backup/back
##             HDD              ##
##################################
${voffset 5}${font DroidSans:bold:size=8}${color4}HDD${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 6}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}ROOT${goto 95}${font DroidSans:size=8.3}${fs_used /}${goto 133}/${offset 5}${fs_size /}${alignr}${fs_free /}${font}
${voffset 6}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}${if_existing /media/boudiccas/backup}BACKUP: ${goto 95}${font DroidSans:size=8.3}${fs_used /media/boudiccas/backup}${goto 133}/${offset 5}${else} BACKUP:  Not Mounted${endif}${fs_size /media/boudiccas/backup}${alignr}${fs_free /media/boudiccas/backup}${font}
${voffset 6}${font StyleBats:size=9.9}${color2}x${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}${if_existing /media/boudiccas/back4}BACK 4: ${goto 95}${font DroidSans:size=8.3}${color3}${offset 4} ${alignc}${fs_used /media/boudiccas/back4} / ${else} BACKUP 4:  Not Mounted${endif}${fs_size /media/boudiccas/back4}${alignr}${fs_free /media/boudiccas/back4}${font}
${voffset 6}${font StyleBats:size=9.9}${color2}4${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}SWAP${goto 95}${font DroidSans:size=8.3}${swap}${goto 133}/${offset 5}${swapmax}${alignr}${swapperc}%${font}
${voffset 6}${font StyleBats:size=9.9}${color2}4${voffset -2}${font DroidSansFallback:size=8.3}${color3}${offset 4}TRASH: ${goto 133}${execi 60 du -sh ~/.local/share/Trash/files/ | awk '{print $1}' | sed '/^4.0K/ d'  | sed 's/$/ of TRASH /'}${font}
##################################
##         TOP PROCESSES        ##
##################################
#${voffset 5}${font DroidSans:bold:size=8}${color4}TOP PROCESSES${offset 8}${color8}${voffset -2}${hr 2}${font}
#NAME              PID    CPU     MEM
#${top name 1}${alignr} ${top pid 1} ${top cpu 1}% ${top mem 1}%
#${top name 2}${alignr} ${top pid 2} ${top cpu 2}% ${top mem 2}%
#${top name 3}${alignr} ${top pid 3} ${top cpu 3}% ${top mem 3}%
#${top name 4}${alignr} ${top pid 4} ${top cpu 4}% ${top mem 4}%
#${top name 5}${alignr} ${top pid 5} ${top cpu 5}% ${top mem 5}%
#${top name 6}${alignr} ${top pid 6} ${top cpu 6}% ${top mem 6}%
# |--${font Droid Sans:style=Bold:size=10}Processe${font}
${font arial black:size=10}${color green}PROCESS${color}${font arial black:size=9}LIST${color green} ${hr 2}$color$font
${color white}Processes:$color $processes ${goto 177}${color white}Running:${color red} $running_processes $color
${goto 60}${color green}${font arial black:size=7}CPU-TOP PROCESSES:$font$color
${font arial black:size=7}NAME${goto 100}PID${goto 150}CPU${alignr}MEM $font
${color red}${lua_parse top cpu 1}${color green}${font arial black:size=7}1$color$font. ${color red}${top name 1}${alignr 80}${top pid 1}$color${alignr 35}${color red}${font arial black:size=7}${top cpu 1}$color$font${alignr}${color red}${top mem 1}$color
${lua_parse top cpu 2}${color green}${font arial black:size=7}2$color$font. ${top name 2}${alignr 80}${top pid 2}${alignr 35}${color green}${font arial black:size=7}${top cpu 2}$color$font${alignr}${top mem 2}
${lua_parse top cpu 3}${color green}${font arial black:size=7}3$color$font. ${top name 3}${alignr 80}${top pid 3}${alignr 35}${color green}${font arial black:size=7}${top cpu 3}$color$font${alignr}${top mem 3}
${lua_parse top cpu 4}${color green}${font arial black:size=7}4$color$font. ${top name 4}${alignr 80}${top pid 4}${alignr 35}${color green}${font arial black:size=7}${top cpu 4}$color$font${alignr}${top mem 4}
${goto 60}${color green}${font arial black:size=7}RAM-TOP PROCESSES:$font$color
${font arial black:size=7}NAME${goto 100}PID${goto 150}CPU%${alignr}%MEM $font
${color red}${lua_parse top mem 1}${color green}${font arial black:size=7}1$color$font. ${color red}${top_mem name 1}${alignr 80}${top_mem pid 1}${alignr 35}${top_mem cpu 1}$color${alignr}${color red}${font arial black:size=7}${top_mem mem 1}$color$font
${lua_parse top mem 2}${color green}${font arial black:size=7}2$color$font. ${top_mem name 2}${alignr 80}${top_mem pid 2}${alignr 35}${top_mem cpu 2}$color${alignr}${color green}${font arial black:size=7}${top_mem mem 2}
${lua_parse top mem 3}${color green}${font arial black:size=7}3$color$font. ${top_mem name 3}${alignr 80}${top_mem pid 3}${alignr 35}${top_mem cpu 3}${alignr}${color green}${font arial black:size=7}${top_mem mem 3}$color$font
${lua_parse top mem 4}${color green}${font arial black:size=7}4$color$font. ${top_mem name 4}${alignr 80}${top_mem pid 4}${alignr 35}${top_mem cpu 4}${alignr}${color green}${font arial black:size=7}${top_mem mem 4}$color$font
#${lua_parse top mem 5}${color green}${font arial black:size=7}5$color$font. ${top_mem name 5}${alignr 80}${top_mem pid 5}${alignr 35}${top_mem cpu 5}${alignr}${color green}${font arial black:size=7}${top_mem mem 5}$color$font
##################################
##           NETWORK            ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}NETWORK${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}T${font DroidSans:size=8.65}${color3}${offset 5}Download${goto 120}${font DroidSans:size=8.3}${totaldown eth0}${alignr}${font DroidSans:size=8.3}${downspeed eth0}${font}
${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}N${font DroidSans:size=8.65}${color3}${offset 5}Upload${goto 120}${font DroidSans:size=8.3}${totalup eth0}${alignr}${font DroidSans:size=8.3}${upspeed eth0}${font}
${voffset 4}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Private${offset 3}IP${goto 123}${font DroidSansFallback:size=8.5}LAN${alignr}${font DroidSans:size=8.3} ${alignr} ${addr eth0}${font}
${voffset 0}${font PizzaDudeBullets:size=9.5}${color6}a${font DroidSans:size=8.65}${color3}${offset 5}Public${offset 7}IP${goto 121}${font DroidSansFallback:size=8.5}WAN${alignr}${font DroidSans:size=8.3} ${alignr} ${execi 1800 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}${font}
##################################
##     WEATHER (Imperial)       ##
##################################
#${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
#${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 /home/boztu/.conky/weather/weather.sh "Scottsdale,AZ" ctbi}${font}${voffset -28}${goto 33}${font Weather:size=42}${color3}y${font}
#${voffset -38}${font Ubuntu:size=8.63}${color5}${execi 1800 /home/boztu/.conky/weather/weather.sh "Scottsdale,AZ" ctti}${font}
#${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
#${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 /home/boztu/.conky/weather/weather.sh "Scottsdale,AZ" ccb}${font}
#${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/boztu/.conky/weather/weather.sh "Scottsdale,AZ"}${font}
#${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/boztu/.conky/weather/weather.sh "Scottsdale,AZ" cp}${font}
#${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/boztu/.conky/weather/weather.sh "Scottsdale,AZ" dl}${font}
#${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/boztu/.conky/weather/weather.sh "Scottsdale,AZ" fcp}${font}
#${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 28}${execi 1800 /home/boztu/.conky/weather/weather.sh "Scottsdale,AZ" fcti}${font}
##################################
##      WEATHER (Metric)        ##
##################################
# ${voffset 4}${font DroidSans:bold:size=8.25}${color4}WEATHER${offset 8}${color8}${voffset -2}${hr 2}${font}
# ${voffset -55}${font RadioSpace:size=34}${color3}${execi 1800 /home/boztu/.conky/weather/weather.sh "Toronto" ctbm}${font}${voffset -28}${goto 33}${font Weather:size=42}${color3}y${font}
# ${voffset -38}${font Ubuntu:size=8.63}${color5}${execi 1800 /home/boztu/.conky/weather/weather.sh "Toronto" cttm}${font}
# ${voffset -39}${font KRARound:size=36}${color3}${goto 195}I${font}
# ${voffset 6}${font Ubuntu:size=23}${color5}${alignc -2}${execi 1800 /home/boztu/.conky/weather/weather.sh "Toronto" ccb}${font}
# ${voffset 8}${font DroidSansFallback:size=8.63}${color3}${execi 1800 /home/boztu/.conky/weather/weather.sh "Toronto"}${font}
# ${voffset -57}${font ConkyWeather:size=48}${color6}${alignc -55}${execi 1800 /home/boztu/.conky/weather/weather.sh "Toronto" cp}${font}
# ${voffset 6}${font DroidSansMono:bold:size=8.62}${color4}${offset 40}${execi 1800 /home/boztu/.conky/weather/weather.sh "Toronto" dl}${font}
# ${voffset 0}${font ConkyWeather:size=37.9}${color3}${offset 26}${execi 1800 /home/boztu/.conky/weather/weather.sh "Toronto" fcp}${font}
# ${voffset 0}${font DroidSansFallback:bold:size=8.62}${color4}${offset 35}${execi 1800 /home/boztu/.conky/weather/weather.sh "Toronto" fctm}${font}
##################################
##             TIME             ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}TIME${offset 8}${color8}${voffset -2}${hr 2}${font}
#${voffset -4}${font RadioSpace:size=32}${color3}${if_match ${time %l}<=9}${alignc 7}${time %l:%M%p}${else}${if_match ${time %l}>=10}${alignc -1}${time %l:%M%p}${endif}${endif}${font}
${voffset -4}${font RadioSpace:size=32}${color3}${alignc -1}${time %H:%M:%S}${font}
##################################
##      CALENDAR (5-Line)       ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}DATE${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset 2}${font DroidSansMono:size=10}${color3}${alignc}${time %a }${time %e %B %G}${font}
#${voffset -4}${font DroidSansFallback:bold:size=18}${if_match ${time %e}<=9}${color5}${alignc 65}${time %e}${font}${else}${if_match ${time %e}>=10}${color5}${alignc 60}${time %e}${endif}${endif}${font}
#${voffset 0}${font DroidSansMono:size=7.55}${color3}${alignc 60}${time %B}${font}
#${voffset 0}${font DroidSansMono:size=7.6}${color3}${alignc 60}${time %Y}${font}
#${voffset -83}${font CutOutsFor3DFX:size=67}${color8}${alignc 99}2${font}
####
## Uncomment for Conky 1.8.0 (use mono fonts only)
# ${voffset -68}${font DroidSansMono:size=7.55}${color3}${execpi 60 #boztu_Cal_9=`date +%-d`; cal -h | sed -e 's/\r//g' -e 's/^/ /g' #-e '1d' -e s/^/"\$\{offset 100"\}/ -e #'s/\<'"$boztu_Cal_9"'\>/${color4}&${color3}/'}
####
## Uncomment for Conky 1.8.1 (use mono fonts only)
#${voffset -64}${offset 100}${font DroidSansMono:size=7.55}${color3}${execpi 60 boztu_Cal_9=`date +%-d`; cal -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e 's/\<'"$boztu_Cal_9"'\>/${color4}&${color3}/'}
## APT-GET UPDATES ##
${voffset 4}${font DroidSans:bold:size=8}${color4}APT-GET UPDATES${offset 8}${color8}${voffset -2}${hr 2}${font}
APT-GET: ${execi 300 apt-get -s upgrade|grep installed|cut -d' ' -f1} updates ready
 TODAY:     ${execi 300 vnstat | grep "today" | awk '{print $8 $9}'} / MONTH:     ${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $9 $10}'}


##################################
##             MPD              ##
##################################
${if_running mpd}
${voffset -25}${font DroidSans:bold:size=7.75}${color4}MPD${offset 8}${color8}${voffset -2}${hr 2}${color3}${font}
${voffset 4}$mpd_status
${voffset 4}$mpd_artist
${voffset 4}$mpd_title
${voffset 4}${mpd_bar 5,100}
${voffset 4}$mpd_percent %          $mpd_elapsed/$mpd_length ${alignr} GMAIL:    ${execi 300 python ~/.conky/gmail.py}${endif}


#####################################################################

Lets see how this goes?

Sharon.

---

### Post by boudiccas on 2013-07-05
okay, *how* do you paste code to this thread? I've pasted it as plain-text, and its still screwed up. I've tried putting  before it , paste plain text,  but it still screws up. So, how do you do it then?Sharon.

---

### Post by boudiccas on 2013-07-05
Sorted, don't use 'chromium' use 'google-chrome' instead!

Sharon.

---

### Post by stinkeye on 2013-07-05
Helps to insert in code brackets.
Highlight what you paste and click on the "#" button.

Do you have a problem with conky?

---

### Post by boudiccas on 2013-07-05
No, but it needs slightly out-of -the-ordinary configuration, and thats what I was trying to post.

Sharon.

---

