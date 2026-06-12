---
title: "Conky: three little problems"
date: 2009-11-30
forum: Desktop Environments
---

### Post by demoneivo on 2009-11-30
Hi, 
I have 3 little problems with my conky configuration

1) The first is absolutely noob but I never succed in understanding how to chose the dimension of conky.
For example I have an horizontal conky with this setting

"minimum_size 1280 0"

But if i change the 0, conky panel don't change... How can I change the dimension of it?

2) The second question is: How can I leave conky panel above window
When maximizing windows conky lies under them. I want it like gnome-panel, always above windows

3) Last but not the least: I have a little problems with conky..
When clicking on the desktop, conky goes away and I have to recall it in terminal (terminal--> conky)

Can anyone help me??

This is my .conkyrc
> #Impostazioni di base
double_buffer yes
own_window yes
own_window_transparent no
own_window_type desktop

#Posizione
gap_x 0
gap_y 5
alignment top_left
use_spacer none
minimum_size 1280 0

#Aggiornamento
update_interval 1

#Colori
default_color  707070
own_window_colour 000000

#Font
use_xft yes
xftfont visitor TT2 BRK:size=10

TEXT
${alignc}Distribuzione ${color ffffff}Ubuntu 9.10${color}  Kernel ${color ffffff}$kernel${color}  ${alignc}Hostname ${color ffffff}${nodename}${color}  Uptime ${color ffffff}${uptime_short}${color}  ${alignc}Batteria ${color ffffff}${battery_percent BAT0}%${color}  ${alignc}Remaining Time ${color ffffff}$battery_time${color}  Cpu ${color ffffff}${cpu}%${color}  Ram ${color ffffff}${memperc}%${color}  Hdd ${color ffffff}${fs_used} / ${fs_size}${color}
${alignc}GPU Temp ${color ffffff}${execi 30 nvidia-settings -q [gpu:0]/GPUCoreTemp | grep '):' | awk '{print $4}' | sed 's/\.//'}°C${color}  ${alignc}Local IP ${color ffffff}${addr eth2}${color}  ${alignc}DownSpeed ${color ffffff}${downspeed eth2}${color}  ${alignc}UpSpeed ${color ffffff}${upspeed eth2}${color}  ${alignc}TotDown ${color ffffff}${totaldown eth2}${color}  ${alignc}TotUp ${color ffffff}${totalup eth2}${color}  WiFi Signal ${color ffffff}${wireless_link_qual_perc eth2}%${color}${alignc}

---

### Post by VCoolio on 2009-11-30
Your first issue I don't really understand; the vertical size of your conky is defined by the amount of lines below TEXT, unless you set a bigger minimum-size than that.

For the other two, add / change this:
own_window_type normal
own_window_hints above

Check the [manual]("http://conky.sourceforge.net/docs.html") for more options on those two.

---

### Post by demoneivo on 2009-11-30
Thank's a lot man!

Sorry for my english but I am italian and I have some troubles with your language :(

However your answer to my first question is really clear (I have left a blank row in my .conkyrc and I have seen the text of my concky magically coming down a row)
The second was own_window_type panel in order to maximize windows without hiding conky


Thank's a lot, three problems solved with one answer

---

### Post by demoneivo on 2009-11-30
Sorry, I forgot one little problem with the last line of this part of conkyrc

> ${alignc}Local IP ${color ffffff}${addr eth2}${color}  ${alignc}DownSpeed ${color ffffff}${downspeed eth2}${color}  ${alignc}UpSpeed ${color ffffff}${upspeed eth2}${color}  ${alignc}TotDown ${color ffffff}${totaldown eth2}${color}  ${alignc}TotUp ${color ffffff}${totalup eth2}${color}  [COLOR="Red"]WiFi Signal ${color ffffff}${wireless_link_qual_perc eth2}%${color}${alignc}[/COLOR] 

I can get in conky all the information as Local IP, Download speed, Upload Speed, Total Download Data, Total Upload Data..

The only thing I can't get working is WIFI signal strenght. Do you know why?

---

### Post by VCoolio on 2009-11-30
The panel window type is new in conky, I hadn't thought of that. Then you don't need window_hints anymore of course, clever.
I don't use wifi, so I don't know. But you could ask in [this thread]("http://ubuntuforums.org/showthread.php?t=281865") over here, there are some very bright conky users over there. Oh and your English is fine by the way; it's not my native language either. I just wan't really sure if I had understood you correctly.

---

