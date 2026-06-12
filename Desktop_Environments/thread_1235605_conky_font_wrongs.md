---
title: "conky font wrongs"
date: 2009-08-09
forum: Desktop Environments
---

### Post by ulissess on 2009-08-09
hi , i have configurate ".conkyrc" but i have wrong font!! Instead of thermometer, i have that strange font (on the left of 32°c)! i just try to put the good weather.ttf but it doesn't work! how can i change font?? 

> [...]WEATHER ${hr 2}
XXXXXX:

${if_existing /proc/net/route wlan0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=XXXXXXXX --datatype=WF}${font}
${voffset -50}${font weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=16}${execi 600 conkyForecast --location=XXXXXXXX --datatype=HT}${font} [...]

[IMG]http://img34.imageshack.us/img34/8611/conky.jpg[/IMG]

thank u so much!!

---

