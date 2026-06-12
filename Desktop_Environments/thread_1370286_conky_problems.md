---
title: "conky problems"
date: 2010-01-02
forum: Desktop Environments
---

### Post by Ganjafreak on 2010-01-02
I installed conky, the newest version

I got this error when I edited the .conkyrc and saved it and opened terminal and ran it with conky as the command

error: 
```

ganjafreak@ganjafreak-desktop:~$ conky
Conky: /home/ganjafreak/.conkyrc: 7: no such configuration: 'on_bottom'
Conky: /home/ganjafreak/.conkyrc: 24: config file error
Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none.
Conky: diskio device '/sda' does not exist
Conky: diskio device '/sdb' does not exist
Conky: statfs '/media/1000go': No such file or directory
Conky: statfs '/media/300go': No such file or directory
Conky: statfs '/media/temp': No such file or directory
Conky: forked to background, pid is 11659
ganjafreak@ganjafreak-desktop:~$ 
Conky: desktop window (14000a9) is subwindow of root window (156)
Conky: window type - normal
Conky: drawing to created window (0x4400001)
Conky: drawing to double buffer
Conky: statfs '/media/temp': No such file or directory
Conky: statfs '/media/300go': No such file or directory
Conky: statfs '/media/1000go': No such file or directory
Conky: attempting to use more CPUs than you have!
obj->data.cpu_index 2 info.cpu_count 1


```

```
#emplacement
alignment top_left
# set to yes if you want Conky to be forked in the background
background yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
use_xft yes
on_bottom no
xftfont sans :size=8
xftalpha 0.8
update_interval 2.0
total_run_times 0
own_window yes
#type de fenetre : normal(avec le cadre) / override / desktop
#own_window_type override
own_window_transparent yes
double_buffer yes
minimum_size 230 0
draw_shades no
draw_outline no
draw_borders no
stippled_borders 0
border_margin 10
border_width 3
default_color #454451
default_shade_color black
default_outline_color black
alignment top_right
# ecart avec le bord x=gauche ou droit y= haut ou bas
gap_x 15
gap_y 0
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
use_spacer no

#Affichage des accents et caractÃ¨res spÃ©ciaux :
override_utf8_locale yes

TEXT
${font Sans:size=9:weight=bold}${color  #99CBFF}${hr 2}$color${font Sans:size=8:weight=bold}
${alignc 30}${color #E67B13}${font OpenLogos:size=50}o${font}
${color #F3A312}${font arial :size=14}$alignc .::Coyotus::. ${font sans :size=08}
${color #00ffed}$stippled_hr
${color #F3A312}Uptime:$color $alignr$uptime ${color #FFFFFF}
${color #F3A312}CPU UtilisÃ© : ${color #FFFFFF}$alignr Intel(R) Quad(R) Core i7 920 CPU 2.66GHz
${color #F3A312}Core 1: ${color #FFFFFF}${freq cpu1}Mhz $alignr${color #F3A312}Core 2: ${color #FFFFFF}${freq cpu2}Mhz
${color #00ffed}${cpubar cpu1 5,85} :${cpu cpu1}%  $alignr${cpubar cpu2 5,85} :${cpu cpu2}%
${color #F3A312}${cpugraph cpu1 26,150 00ffed 00ffed}$alignr${cpugraph cpu2 26,150 00ffed 00ffed}${font sans :size=12}
${color #FFFFFF}${alignc}H@CK3R WAY OF LIFE$font
${color #00ffed}$stippled_hr
${color #e49c16}MÃ©moire RAM :${color #FFFFFF} $alignr$mem/$memmax - $memperc%
${color #00ffed}${membar}
${color #e49c16}MÃ©moire SWAP :${color #FFFFFF} $alignr$swap/$swapmax - $swapperc%
${color #00ffed}${swapbar}
${color #00ffed}$stippled_hr
${color #e49c16}Processus : ${color #FFFFFF}${color}$processes ${color #e49c16}En cours : ${color #FFFFFF}${color}$running_processes ${color #e49c16}$alignr(%)  CPU   MEM
  ${color #FFFFFF}${top name 1} $alignr${top cpu 1} ${top mem 1}
  ${color #CCCCCC}${top name 2} $alignr${top cpu 2} ${top mem 2}
  ${color #FFFFFF}${top name 3} $alignr${top cpu 3} ${top mem 3}
  ${color #CCCCCC}${top name 4} $alignr${top cpu 4} ${top mem 4}
  ${color #e49c16}Memoire :${color #e49c16}$alignr (%)  CPU   MEM
  ${color #FFFFFF}${top_mem name 1} $alignr${top_mem cpu 1} ${top_mem mem 1}
  ${color #CCCCCC}${top_mem name 2} $alignr${top_mem cpu 2} ${top_mem mem 2}
  ${color #FFFFFF}${top_mem name 3} $alignr${top_mem cpu 3} ${top_mem mem 3}
${color #00ffed}$stippled_hr
${color #e49c16}IP Locale : ${color white}${addr eth0} $alignr${color #e49c16} IP Publique : ${color white}${execi 1800 ~/.conky/scriptip.sh}
${color #e49c16}Download :${color white} ${downspeed eth0} k/s${color white}${offset 75}${color #e49c16}Upload:${color white} ${upspeed eth0} k/s
${color #F3A312}${downspeedgraph eth0 26,150 00ffed 00ffed} $alignr${color #F3A312}${upspeedgraph eth0 26,150 00ffed 00ffed}
${color #00ffed}${totaldown eth0}$alignr${totalup eth0}
${color #e49c16}Connection(s) : $alignr${color #FFFFFF}entrante(s) : ${color}${tcp_portmon 1 32767 count}
$alignr${color white}sortante(s) : ${color #FFFFFF}${color}${tcp_portmon 32768 61000 count}$alignr
$alignr${color white}total : ${color #FFFFFF}${color}${tcp_portmon 1 65535 count}
${color #00ffed}$stippled_hr
${font sans :size=10}${color #FFFFFF}${alignc}Disques Dur$font
${font sans :size=8}${color #FFFFFF}Disques           Temperature${alignr}Debit IO$font
${color #FFFFFF}/dev/hda :${color #00ffed}               ${hddtemp /dev/sda}${alignr}${diskio /sda}
${color #FFFFFF}/dev/hdc :${color #00ffed}               ${hddtemp /dev/sdb}${alignr}${diskio /sdb}
${color #00ffed}$stippled_hr
${color #e49c16}Espace Disque :
${color white}Ubuntu: ${color #00ffed}${color #FFFFFF}$alignr${fs_free /}/${fs_size /} ${color #00ffed}
${fs_bar /}
${color white}1000 go:  ${color #00ffed}${color #FFFFFF}$alignr${fs_free /media/1000go}/${fs_size /media/300go} ${color #00ffed}
${fs_bar /media/1000go}
${color white}Temp:  ${color #00ffed}${color #FFFFFF}$alignr${fs_free /media/temp}/${fs_size /media/temp} ${color #00ffed}
${fs_bar /media/temp}
```

---

### Post by VCoolio on 2010-01-02
> **Ganjafreak said:**
> I installed conky, the newest version

I got this error when I edited the .conkyrc and saved it and opened terminal and ran it with conky as the command

error: 
```

ganjafreak@ganjafreak-desktop:~$ conky
Conky: /home/ganjafreak/.conkyrc: 7: no such configuration: 'on_bottom'
Conky: /home/ganjafreak/.conkyrc: 24: config file error
Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none.
Conky: diskio device '/sda' does not exist
Conky: diskio device '/sdb' does not exist
Conky: statfs '/media/1000go': No such file or directory
Conky: statfs '/media/300go': No such file or directory
Conky: statfs '/media/temp': No such file or directory
Conky: forked to background, pid is 11659
ganjafreak@ganjafreak-desktop:~$ 
Conky: desktop window (14000a9) is subwindow of root window (156)
Conky: window type - normal
Conky: drawing to created window (0x4400001)
Conky: drawing to double buffer
Conky: statfs '/media/temp': No such file or directory
Conky: statfs '/media/300go': No such file or directory
Conky: statfs '/media/1000go': No such file or directory
Conky: attempting to use more CPUs than you have!
obj->data.cpu_index 2 info.cpu_count 1

```


If you read the error messages you should be able to figure out much yourself. 
On line 7: no such configuration: there is no on_bottom setting, so delete that line.
On line 24: config file error: You have default_color #454451 there, but the '#' comments what follows; you need to specify html-colorcodes without the usual preceding '#' (you also do that below the TEXT line)
The rest explains itself: you have no usb devices and files or paths like specified below 'TEXT'; also the config is for multiple processor pc's, so change the lines with cpu1 and cpu2 accordingly (just use 'cpu' instead).

Manual with options you can find [here]("http://conky.sourceforge.net/docs.html"); a great conky site [here]("http://conky.linux-hardcore.com/") and a big thread where you can show off and ask questions [here]("http://ubuntuforums.org/showthread.php?t=281865").

---

### Post by Ganjafreak on 2010-01-02
I had to remove alot more than that because it said I had no temp and no 300g or 1000g or whatever that is, I do have a TEMP folder so wtf, It also keep talking about more cpu's than you have! so I removed that cpu bit and to get it to work I deleted alot of stuff it needed and got this

[http://img188.imageshack.us/img188/1337/screenshotrk.png](http://img188.imageshack.us/img188/1337/screenshotrk.png)

---

### Post by Ganjafreak on 2010-01-02
Okay,

I got 

```
ganjafreak@ganjafreak-desktop:~$ conky
Conky: /home/ganjafreak/.conkyrc: 33: no such configuration: 'cpu'
Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none.
Conky: can't parse X color '${color #FFFFFF}${alignc}H@CK3R WAY OF LIFE$font
${color #00ffed}$stippled_hr
${color #e49c16}MÃ©moire RAM :${color #FFFFFF} $alignr$mem/$memmax - $memperc%
${color #00ffed}${membar}
${color #e49c16}MÃ©moire SWAP :${color #FFFFFF} $alignr$swap/$'
Conky: forked to background, pid is 22339
ganjafreak@ganjafreak-desktop:~$ 
Conky: desktop window (14000a9) is subwindow of root window (156)
Conky: window type - normal
Conky: drawing to created window (0x4e00001)
Conky: drawing to double buffer


```

Now do note, it says that file isn't there the /home/ganjafreak/.conkyrc well it is, I can type /home/ganjafreak/.conkyrc into the bar and it says this file name is already in use.

I just want to have this conky on my desktop why is it being so hard.

[http://linux-hardcore.com/index.php?PHPSESSID=8b46607261268bc3c9b947d1d1dfec6a&topic=1879.0](http://linux-hardcore.com/index.php?PHPSESSID=8b46607261268bc3c9b947d1d1dfec6a&topic=1879.0)

All those extra files and folders that it says you need I already have, I have a folder called Conky in /home/ganjafreak/ it has googlecal scripts folder all that.

---

### Post by VCoolio on 2010-01-02
You still need to remove '#' from the colors. Also on line 33 you seem to have something starting with 'cpu' which conky doesn't understand. Check my manual link for the available options.
For temperature stuff try [this]("https://help.ubuntu.com/community/SensorInstallHowto"): install lm-sensors, run "sudo sensors-detect", say yes to all questions and then in conky use a command like
${execi 10 sensors | grep CPU | awk '{print $3}'}

Also, don't look at it as 'hard', but as 'fun', which it is. Actually it's not that hard, just scroll a bit through the manual and build your own conky config step by step instead of wrestling to get a config to work that was written for another kind of pc.

---

### Post by Ganjafreak on 2010-01-03
I fugred it out, I had to remove the extra CPU meter and change cpu_samples 2 to 1. Then it worked.

---

