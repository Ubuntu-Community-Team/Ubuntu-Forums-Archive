---
title: "Where I can download good gdesklets ?"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by chakkaradeep on 2007-04-20
Hi All,

Where I can download good gdesklets :)

---

### Post by Ownerizer on 2007-04-20
If you're looking to install gdesklets, open a terminal window and run the following command:
**sudo apt-get install gdesklets**

If you want to find more desklets to use in the program, you could check out:
[http://www.gdesklets.de/?q=desklet/browse]("http://www.gdesklets.de/?q=desklet/browse")

Hope that helps! :-)

---

### Post by chakkaradeep on 2007-04-20
> **Ownerizer said:**
> 
[http://www.gdesklets.de/?q=desklet/browse]("http://www.gdesklets.de/?q=desklet/browse")


Thanks :) 

Why are they so less. I didnt find anything quite interesting ! :(

---

### Post by orb9220 on 2007-04-20
[http://gdesklets.zencomputer.ca/](http://gdesklets.zencomputer.ca/)
[http://gdesklets.de/](http://gdesklets.de/)

---

### Post by papercuts on 2007-04-20
In my opinion most of the gdesklets are useless and they mostly look horrible. It doesn't even compare to the similar applications on other systems. I installed a few but the clock was the only one I liked.  So I decided it's not worth installing even.

---

### Post by orb9220 on 2007-04-20
Yep you hit the desklet on the head.

I use 1 clock and good weather applet that actually works and that is it.
and there is a linux version of rainlendar for my calendar,todo,appts

---

### Post by chakkaradeep on 2007-04-20
> **papercuts said:**
> In my opinion most of the gdesklets are useless and they mostly look horrible. It doesn't even compare to the similar applications on other systems. I installed a few but the clock was the only one I liked.  So I decided it's not worth installing even.

Exactly and thats the reason I was searching but in ended up in vain :(

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

### Post by papercuts on 2007-04-28
Try Screenlets instead. Search this forum and you'll find your way. I tried that and it's far better than gdesklets in terms of looks and ease of use.

---

### Post by sorcererx84 on 2007-04-29
Installation instructions can be found at [http://hendrik.kaju.pri.ee/screenlets/?q=node/5](http://hendrik.kaju.pri.ee/screenlets/?q=node/5)

---

