---
title: "gdesklets help please....."
date: 2007-03-05
forum: Desktop Environments
---

### Post by ginnie6 on 2007-03-05
I've got gdesklets installed and I'm trying to put the weather one on my desktop. It goes on but it says failed on connecting to get temps. Any ideas?


Thanks!!!

---

### Post by 13217495 on 2007-04-22
Yahoo's website has changed the page layout so I rewrote the regular expressions if you want some of the weather desklets to work replace the code with the below in the __init__.py file in the /usr/share/gdesklets/Sensor/weather directory


RE_TEMPERATURE = re.compile("<h3>(?P<temp>\d+)&deg;</h3>")
RE_TEMPERATURE_HI = re.compile("")
RE_TEMPERATURE_LO = re.compile("")
RE_TEMPERATURE_FEEL = re.compile("<dt>Feels Like:</dt>\n<dd>(?P<temp_feel>\d+)&deg;</dd>")
RE_PRESSURE = re.compile("<dt>Barometer:</dt>\n<dd>\n(?P<pressure>[\d\.]+) \w+ \nand (?P<pressure_change>.+)\n")
RE_DEWPOINT = re.compile("<dt>Dewpoint:</dt>\n<dd>(?P<dewpoint>\d+)&deg;</dd>")
RE_WIND = re.compile("<dt>Wind:</dt>\n<dd>(?P<wind>[\w\s]+)</dd>")
RE_HUMIDITY = re.compile("<dt>Humidity:</dt>\n<dd>(?P<humidity>\d+)\%")
RE_SUNRISE = re.compile("<dt>Sunrise:</dt>\n<dd>(?P<sunrise>.+)</dd>")
RE_SUNSET = re.compile("<dt>Sunset:</dt>\n<dd>\n(?P<sunset>.+)</dd>")
RE_VISIBILITY = re.compile("<dt>Visibility:</dt>\n<dd>\n(?P<visibility>\S+)")
RE_SKY = re.compile("</em>\n<h3>(?P<sky>[^\<]+)</h3>")
RE_ICON = re.compile("http://us.i1.yimg.com/us.yimg.com/i/us/nws/weather/gr/(?P<icon>\d+)\D.png")
RE_MATCHES = re.compile("Weather location matches:\</font\>\</td\>\n\s*\</tr\>\</table\>\n\s*\<font face=\"arial\" size=-1\>\n\s*\<ul\>\n\s*\<li\>\n\s*\<a href=\"(?P<matchurl>[^\"]+)\"\>")

---

### Post by orb9220 on 2007-04-23
> **ginnie6 said:**
> I've got gdesklets installed and I'm trying to put the weather one on my desktop. It goes on but it says failed on connecting to get temps. Any ideas?


Thanks!!!

Get the good weather desklet here:

[http://gdesklets.zencomputer.ca/](http://gdesklets.zencomputer.ca/)

Works great

---

