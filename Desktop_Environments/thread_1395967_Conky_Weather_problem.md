---
title: "Conky Weather problem"
date: 2010-02-01
forum: Desktop Environments
---

### Post by TyD on 2010-02-01
I'm trying to configure conky to update me on the local weather using the conkyForecast script.  I added the below section of code to my .conkyrc file, but when I run conky I don't get any forecast data.  

```
WEATHER ${hr 2}
${voffset 0}${font}Wind Speed: ${alignr}${execi 600 conkyForecast --location=USNC0558 --hideunits --datatype=WS} km/h ${execi 600 conkyForecast --location=USNC0558 --hideunits --datatype=WD}
${voffset 0}Daylight: ${alignr}${execi 600 conkyForecast --location=USNC0558 --datatype=SR} ~ ${execi 600 conkyForecast --location=USNC0558 --datatype=SS}

${font Trebuchet MS:size=12}${execi 600 conkyForecast --location=USNC0558 --datatype=MP}
${voffset -30}${alignr 42}${font MoonPhases:size=28}${execi 600 conkyForecast --location=USNC0558 --datatype=MF}${font}
```Any help would be greatly appreciated.

---

### Post by Barriehie on 2010-02-02
I've got this in my ~/.conkyrc and it works fine.  You'll have to change the paths for weather and weather1.

```

${color white}${rss http://rss.accuweather.com/rss/liveweather_rss.asp?metric=0&locCode=89110 120 item_title 0}${color cyan}${execi 120 curl "http://rss.accuweather.com/rss/liveweather_rss.asp?metric=0&locCode=89110">/home/barrie/weather && sed -i 's/&/\n/g' /home/barrie/weather && sed -i 's/>/\n/g' /home/barrie/weather && grep -i high: /home/barrie/weather>/home/barrie/weather1}
${rss http://rss.accuweather.com/rss/liveweather_rss.asp?metric=0&locCode=89110 120 item_title 1}
${head /home/barrie/weather1 1 120}
${rss http://rss.accuweather.com/rss/liveweather_rss.asp?metric=0&locCode=89110 120 item_title 2}
${tail /home/barrie/weather1 1 120}

```

HTH,
Barrie

---

