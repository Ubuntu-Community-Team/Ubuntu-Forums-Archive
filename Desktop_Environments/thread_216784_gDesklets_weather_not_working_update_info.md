---
title: "gDesklets weather not working update info"
date: 2006-07-16
forum: Desktop Environments
---

### Post by orb9220 on 2006-07-16
Taken from gDesklet forums

14.07.2006	Weather Sensor Problem?

	Running 0.35.3 on Ubuntu 6.06 (Dapper).

I'm getting "Retrieval Failed" on the lt Weather display.

I took a look at the Weather sensor source code. Has the format of the Yahoo weather page changed in a way that broke the sensor? A "view source" on the Yahoo weather page does look diferent than the regexs in the sensor. For example the sensor has font tags througout it and it looks like the Yahoo page is using CSS.

This used to work but broke within the last few days. Anyone else having problems with the Weather sensor?
	
14.07.2006	re:
dunn
	i am glad i am not the only one having this problem. i have tried all of the weather programs i could find... all of them have the same result.

I have heard of a gdesklet called iWeather. i guess it uses weather.com to load the weather. i cannot find this program. any help would be much appreciated.

-Danny

It seems it was Yahoo weather changing thier layout.

---

### Post by Thund3rstruck on 2006-07-16
Same here, my gf and I are both using that applet and it's a shame it stopped working...

---

### Post by T_W on 2006-07-16
I also started a thread on this over here:

[http://www.ubuntuforums.org/showthread.php?t=215769](http://www.ubuntuforums.org/showthread.php?t=215769)

No resolution yet in either forum. 

I tried to hand modify the Weather sensor, but didn't have any luck.

---

### Post by simontol on 2006-11-27
Same problem here too...
I tried to compile gdesklets-0.35.4 from sources but the problem not solved...
I think it's a sensor problem.
Someone please help!!!

---

### Post by clyde9999 on 2006-11-27
Here is an easy solution to the problem. Right click on the gdesklet icon in the system tray, Click on &#8220;Manage Desklets&#8221;. Leave it to the side. Then open your browser. Go to [http://gdesklets.zencomputer.ca/](http://gdesklets.zencomputer.ca/) Then scroll down to the &#8220;GoodWeather&#8221; desklet and drag the checked desklet to your opened desklet manager. It will probably store in the &#8220;uncategorized&#8221; folder. But will show up for you to double click it to install it to your desktop. It is very easy. Then to configure it, right click on the desklet, then enter your zipcode where it says &#8220;location code&#8221; choose how often, in minutes, you wish for it to hit the weather site, choose C or F. done!

Have Fun.

Jack

---

### Post by BLTicklemonster on 2007-01-02
Excellent! Thank you for posting this. That weather thing has been driving me crazier. ](*,)

---

### Post by itsjustarumour on 2007-01-03
BLTicklemonster - GREAT NEWS!!!!

See - [http://www.gdesklets.org/](http://www.gdesklets.org/) - looks like the new gDesklets version is FINALLY on the way!

Hopefully there will be fixes for those Yahoo weather controls.... :D

---

### Post by BLTicklemonster on 2007-01-03
Figures. Right when I don't have intardnet at the house, too.


I'll check. Thanks for the heads up!

---

### Post by ftmichael on 2007-04-09
Just a note that gDesklets weather is still not working, but the [http://gdesklets.zencomputer.ca/](http://gdesklets.zencomputer.ca/) fix still works perfectly!

Michael

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

### Post by itsjustarumour on 2007-05-12
> **13217495 said:**
> Yahoo's website has changed the page layout so I rewrote the regular expressions if you want some of the weather desklets to work replace the code with the below in the __init__.py file in the /usr/share/gdesklets/Sensor/weather directory


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

Has anybody got this script to work?

If so - could you possibly post up a copy of your __init__.py file for me? 

Thanks in advance  :-)

---

### Post by itsjustarumour on 2007-05-15
> **itsjustarumour said:**
> Has anybody got this script to work?

If so - could you possibly post up a copy of your __init__.py file for me? 

Thanks in advance  :-)

BUMP.

---

### Post by orb9220 on 2007-05-15
[http://gdesklets.zencomputer.ca/](http://gdesklets.zencomputer.ca/)

Just go there and get the good weather applet. It works.

---

### Post by mneumonic on 2007-05-15
I dont know if this will help anyone but i got my weather desklet from here [http://www.gdesklets.org/?q=desklet/browse](http://www.gdesklets.org/?q=desklet/browse) uses weather.com i believe .install desklet and go to configure then just go to web page type in weather for your hom location and take the numbered code for your location out of browser bar and add it for location in desklet ... hope that helps or even makes sense

---

### Post by itsjustarumour on 2007-05-16
> **orb9220 said:**
> [http://gdesklets.zencomputer.ca/](http://gdesklets.zencomputer.ca/)

Just go there and get the good weather applet. It works.


orb9220 - thanks for your post, but I already have that one!  I was just trying to get these particular gDesklets working because they matched my theme....

:-)

---

### Post by itsjustarumour on 2007-05-23
BUMP.

Anyone got the above script to work?

---

### Post by erfahren on 2007-07-25
that fix didn't work for me, my city comes up as "ambiguous" which is odd since it's a major US city. 

In any event, I found another good weather desklet on the internet that works well and wanted to post it in the forums here. [http://www.technetra.com/writings/archive/2007/04/20/updated-weather-gdesklets](http://www.technetra.com/writings/archive/2007/04/20/updated-weather-gdesklets)

---

### Post by mcwtlg on 2008-05-03
> **erfahren said:**
> that fix didn't work for me, my city comes up as "ambiguous" which is odd since it's a major US city. 

In any event, I found another good weather desklet on the internet that works well and wanted to post it in the forums here. [http://www.technetra.com/writings/archive/2007/04/20/updated-weather-gdesklets](http://www.technetra.com/writings/archive/2007/04/20/updated-weather-gdesklets)

Had trouble with this one but GoodWeather works well enough.

Thanx all.

---

### Post by peacewithall on 2008-05-07
Anyone having problems with Goodweather now, it seems to have stopped working for me, for the past few days :(.

---

### Post by john6of6 on 2008-05-07
Yeah, it is not just you.  I have it running on three different desktops and they have all stopped loading/updating.  :(

---

### Post by Dagahk on 2008-05-07
Here: [http://ubuntuforums.org/showthread.php?t=784885&highlight=weather](http://ubuntuforums.org/showthread.php?t=784885&highlight=weather)

---

