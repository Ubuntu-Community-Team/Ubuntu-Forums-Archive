---
title: "Configurating ConkyForecast"
date: 2009-11-01
forum: Desktop Environments
---

### Post by acrocephalus on 2009-11-01
Hello!
I have a couple of problems when configurating my ConkyForecast. I attach the code used and a screenshot. First of all, you can see that there is a huge "y" beside the 22ºC, while according to the place from where I took the code there should be a thermometer. I've been trying with the fonts, but I don't see what's happening. The other issue is that I would like to know how can I align the temperature under the weather symbols. Any idea?
Cheers! ;)

```
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=SPXX0038 --datatype=WF}${font}
${voffset -50}${font Weather:size=40}y${font} ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=SPXX0038 --datatype=HT}${font}
${voffset 0}${alignc 43}${execpi 600 conkyForecast --location=SPXX0038 --datatype=DW --startday=1 --shortweekday} ${alignc 8}${execpi 600 conkyForecast --location=SPXX0038 --datatype=DW --startday=2 --shortweekday} ${alignc -29}${execpi 600 conkyForecast --location=SPXX0038 --datatype=DW --startday=3 --shortweekday} ${alignc -64}${execpi 600 conkyForecast --location=SPXX0038 --datatype=DW --startday=4 --shortweekday}
${voffset 0}${alignc 75}${font ConkyWeather:size=28}${execpi 600 conkyForecast --location=SPXX0038 --datatype=WF --startday=1 --endday=4 --spaces=1}${font}
${voffset 0}${font DejaVu Sans:size=7}${alignc 48}${execpi 600 conkyForecast --location=SPXX0038 --datatype=HT --startday=1 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SPXX0038 --datatype=LT --startday=1 --hideunits --centeredwidth=3} ${alignc -14}${execpi 600 conkyForecast --location=SPXX0038 --datatype=HT --startday=2 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SPXX0038 --datatype=LT --startday=2 --hideunits --centeredwidth=3} ${alignc -40}${execpi 600 conkyForecast --location=SPXX0038 --datatype=HT --startday=3 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SPXX0038 --datatype=LT --startday=3 --hideunits --centeredwidth=3} ${alignr 6}${execpi 600 conkyForecast --location=SPXX0038 --datatype=HT --startday=4 --hideunits --centeredwidth=3}/${execpi 600 conkyForecast --location=SPXX0038 --datatype=LT --startday=4 --hideunits --centeredwidth=3}${font}
```
[IMG]http://lh3.ggpht.com/_ATkVc36Tz8k/Su2qpVREZgI/AAAAAAAAI2E/r1hYpZnSNZA/s512/Screenshot.png[/IMG]

---

### Post by gerein on 2010-04-24
You must copy the weather.ttf font that is available in conkycolors and some other packages to /usr/share/fonts and then rebuild your font cache with:

sudo fc-cache -f -v

---

