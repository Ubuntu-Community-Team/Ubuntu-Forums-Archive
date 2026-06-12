---
title: "Need simple conky weather script with basic icons/1-2 days forecast...newbie..."
date: 2009-07-26
forum: Desktop Environments
---

### Post by vickoxy on 2009-07-26
Hi,
so i made my first conky, but would like to have that cool weather also in it.

Found here lot of scripts:
[http://ubuntuforums.org/showthread.php?t=281865&highlight=weather](http://ubuntuforums.org/showthread.php?t=281865&highlight=weather)

but for me as newbie it is all a little bit difficult. So if anyone can point me simple script/how to ...
Like to have some simple/minimalistic icons in it...:D

---

### Post by VCoolio on 2009-07-26
Use this: [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328), it requires some steps (install the scripts, register at weather.com, add your location and add to conkyrc) but I wouldn't know anything easier.

---

### Post by vickoxy on 2009-07-26
Thanks for suggestion, but that seems to complicated for me. E.G. i do not even know whre to find my local codes (Vienna, Austria). I registered at weather.com, but i am to affraid to go on with this installation...

---

### Post by vickoxy on 2009-07-26
Ok-i did it following instructions here:
[http://www.sakharin.com/?q=node/6](http://www.sakharin.com/?q=node/6)
(which are little simplified instructions form here: 
[http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328) (thanks VCoolio)

Works perfect with LAN Cabel plugged in, but id doesn´t recognize my wifi.

Hope that is easy fix-hope someone can help me to resolve this.

This is weather part:

> WEATHER ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=AUXX0025 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font} ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=AUXX0025 --datatype=HT}${font}
${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=AUXX0025 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=AUXX0025 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=AUXX0025 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=AUXX0025 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=AUXX0025 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=AUXX0025 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=AUXX0025 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=AUXX0025 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=AUXX0025 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=AUXX0025 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=AUXX0025 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=AUXX0025 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=AUXX0025 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${else}${if_existing /proc/net/route eth0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=AUXX0025 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font} ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=AUXX0025 --datatype=HT}${font}
${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=AUXX0025 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=AUXX0025 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=AUXX0025 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=AUXX0025 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=AUXX0025 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 10}${execpi 600 conkyForecast --location=AUXX0025 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=AUXX0025 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=AUXX0025 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=AUXX0025 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=AUXX0025 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=AUXX0025 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 70}${execpi 600 conkyForecast --location=AUXX0025 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=AUXX0025 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font} Weather Unavailable
${endif}

---

### Post by vickoxy on 2009-07-26
I fix it-ha:popcorn::o:P:o:P

Replaced > ${if_existing /proc/net/route wlan0} with > ${if_up eth1}

Thanks!

---

