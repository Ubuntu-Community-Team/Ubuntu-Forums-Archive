---
title: "Weather station hardware and software recommendations"
date: 2008-07-19
forum: Education &amp; Science
---

### Post by BroadArrow on 2008-07-19
Does anyone have any recommendations for Ubuntu-friendly weather station hardware and software?

After Googling I've found some attempts to create open source software reading some personal weather station hardware (usually originally designed for Windows) but haven't found anything that is intended to work with Linux out of the box.

Have I missed it or is there not yet widespread support for an open source solution for home users?

---

### Post by squaregoldfish on 2008-07-20
I've been looking into this recently as well. The closest I came was Weather Display, which works on Linux and supports a wide range of weather stations:

[http://www.weather-display.com/index.php](http://www.weather-display.com/index.php)

As far as I can tell, it's not open source, but it is donation-ware, so you can download it for free and pay up some dough if you like it.

There's also some pretty good forums attached to that site, so you should be able to get some more information there if you need it.

Steve.

---

### Post by mikazo on 2008-07-27
I was going to start a thread about weather station hardware too, but I found this one. I'm interested to know if anyone knows of an online source or supplier for temperature sensors, wind speed gauges, rainfall gauges, etc.

I'm interested in hooking up this type of hardware to my Ubuntu box and maybe writing my own weather software.

---

### Post by aimran on 2008-07-28
I was applying for a job in a windfarm operator and it required knowledge of SCADA. Is this a relevant software for weather stations? I'm all too inexperienced but if it's feedback from sensory equipment than wouldn't SCADA do it? As far as I know I have seen some Linux SCADA programs.

---

### Post by squaregoldfish on 2008-07-28
> **mikazo said:**
> I was going to start a thread about weather station hardware too, but I found this one. I'm interested to know if anyone knows of an online source or supplier for temperature sensors, wind speed gauges, rainfall gauges, etc.

I'm interested in hooking up this type of hardware to my Ubuntu box and maybe writing my own weather software.


I'm not overly experienced at this stuff (I've been thinking of getting a weather station, but haven't got anywhere to put it). However, I believe 1-wire stuff will suit you down to the ground. You can buy all the components individually, and set them up in whatever configuration you want. Most weather station software will interact with 1-wire out of the box, but there's no reason why you shouldn't be able to write your own stuff for it. You can order 1-wire stuff from loads of places online, too.

Check out this site for more info - they even have a book you can buy.

[http://www.weathertoys.net/weathertoys/main.html](http://www.weathertoys.net/weathertoys/main.html)

Steve.

---

### Post by Nick Lake on 2008-08-03
Yeah,

I should think it would be easy enough to read the output from the weather stations yourself. Most sensors interface via a COM port so just read the data stream?

- Nick

---

### Post by mikazo on 2008-08-03
After some searching, I did find a temperature module.

[http://www.alliedelec.com/Search/ProductDetail.aspx?SKU=6710082&MPN=DS1620&R=6710082&SEARCH=6710082&DESC=DS1620]("http://www.alliedelec.com/Search/ProductDetail.aspx?SKU=6710082&MPN=DS1620&R=6710082&SEARCH=6710082&DESC=DS1620")

I've also come up with an idea for my own home-made anemometer. I'll most likely do a write-up on my blog if/when I finish the project.

---

### Post by SixedUp on 2008-08-05
Lots (and lots!) of people use 1-wire interfaces to weather stations because Dallas-Maxim (the people who invented 1-wire) created a cheap self-build weather-station package as a demonstration of their technology. It's still available in basic form (wind direction, speed, temperature) as a kit for about £70 in the UK, or about the same in USD elsewhere. Lots of people have designed additional weather-related interfaces too ... pressure, rainfall, sunlight, humidity, lightning strikes, etc etc. There is a linux virtual filesystem (owfs) that allows you simple file-based access to all the connected one-wire sensors, which makes it very easy to integrate the sensors into any application you want. It also has a big community supporting it, which always helps.

Someone mentioned SCADA ... this is a low-level, highly efficient protocol for exchanging information between sensors and actuators, often where transmission costs are very high (think satellite uplinks, where you are charged by the byte). It's neat, but not something I've seen applied to weather stations - or at any rate, not the ones that we're likely to be playing with!

Hope that helps

---

### Post by jsiei97 on 2008-08-09
> **SixedUp said:**
> There is a linux virtual filesystem (owfs) that allows you simple file-based access to all the connected one-wire sensors, which makes it very easy to integrate the sensors into any application you want. It also has a big community supporting it, which always helps.


Does anyone know the current status on owfs and Ubuntu?
It is not in the repository anyway...

I guess it is build from source that is the option?

/Johan

---

### Post by SixedUp on 2008-08-15
> **jsiei97 said:**
> Does anyone know the current status on owfs and Ubuntu?
It is not in the repository anyway...

I guess it is build from source that is the option?

/Johan

I've not used it with Ubuntu, but I see no reason why you couldn't go the compile from source route with minimal effort.  My only experience has been using it on a reflashed WRT54GL router, and the reflashed firmware (OpenWRT) had repository-based support for it ... see [http://owfs.sourceforge.net/WRT54G.html](http://owfs.sourceforge.net/WRT54G.html).

Would love to hear how you get on with it under Ubuntu though.

---

### Post by jsiei97 on 2008-08-15
> **SixedUp said:**
> I've not used it with Ubuntu, but I see no reason why you couldn't go the compile from source route with minimal effort.  My only experience has been using it on a reflashed WRT54GL router, and the reflashed firmware (OpenWRT) had repository-based support for it ... see [http://owfs.sourceforge.net/WRT54G.html](http://owfs.sourceforge.net/WRT54G.html).

Would love to hear how you get on with it under Ubuntu though.

Well, I compiled it installed it and "mounted a dir" but I quickly found a little disturbing side effect... every time it polled the usb device after new 1wire-data my usb mouse froze for some milliseconds....

So this experiment will quickly move off my desktop computer and into something else maybe another computer, maybe onto a nslu2 or the Atmel NGW100 card I've been playing with... 

Let's see what happens. :roll:


Cheers
Johan

---

### Post by mikazo on 2008-08-24
I came up with an idea for an anemometer. Here's what I have so far.

[http://mikazotechblog.blogspot.com/2008/08/uncompleted-homemade-anemometer.html]("http://mikazotechblog.blogspot.com/2008/08/uncompleted-homemade-anemometer.html")

Any thoughts?

---

### Post by SixedUp on 2008-08-26
> **jsiei97 said:**
> Well, I compiled it installed it and "mounted a dir" but I quickly found a little disturbing side effect... every time it polled the usb device after new 1wire-data my usb mouse froze for some milliseconds....

So this experiment will quickly move off my desktop computer and into something else maybe another computer, maybe onto a nslu2 or the Atmel NGW100 card I've been playing with... 

After my last post I came away with my interest in building a weather station rekindled to the point where I'm going to add it back to the projects list. I already have a project to monitor some temperatures (including a pair of freezers out in the garage), for which one-wire would be ideal, so I can just expand the scope of that project, and piggy-back the weather station onto it. Particularly as the garage would be a reasonable mounting location for the weather station anyway.

I (like you) originally thought of using an nslu2, but it turns out that Viglen are currently running an offer with the UK Ubuntu User group, bringing the price of their MPC-L micro-PC down to £79 delivered, including an upgrade to an 80GB drive. That's less than the price of an nslu2 and drive, and it's x86 compatible; just too good an offer to refuse, so I've ordered one to be my new "garage server".

See [http://www.viglen.co.uk/viglen/Products_Services/Product_Range/Product_file.aspx?Type_Info=Description&eCode=XUBUMPCL&Type=Desktops&GUID=]("http://www.viglen.co.uk/viglen/Products_Services/Product_Range/Product_file.aspx?Type_Info=Description&eCode=XUBUMPCL&Type=Desktops&GUID=") for some specs.

---

### Post by SixedUp on 2008-08-26
> **mikazo said:**
> I came up with an idea for an anemometer. Here's what I have so far.

[http://mikazotechblog.blogspot.com/2008/08/uncompleted-homemade-anemometer.html]("http://mikazotechblog.blogspot.com/2008/08/uncompleted-homemade-anemometer.html")

Any thoughts?

My immediate thought was that it looks good, but the weight of the materials are probably going to mean that you'll struggle to measure low winds because there will be quite a lot of inertia to overcome. You'll also need to find some way to calibrate it if you want to talk about real wind speeds.

[This guy (link)]("http://www.astro.uni-bonn.de/~kbagschi/anemoe.shtml") has home-built one too, but on a much smaller scale, making manual calibration easier. However, he also presents some maths for doing the calibration from 1st principles that might be useful.

---

### Post by Proton Soup on 2008-08-28
the inertia itself would mainly affect the frequency response of the device.  but it may affect the operation more directly by increasing the friction on the bearings.  coefficient of static friction will then determine how small a signal will even move the thing, and coefficient of dynamic friction will determine your error (signal loss).

---

### Post by mips on 2008-08-28
[http://oww.sourceforge.net/hardware.html](http://oww.sourceforge.net/hardware.html)
[http://www.aagelectronica.com/aag/](http://www.aagelectronica.com/aag/)
[http://oww.sourceforge.net/](http://oww.sourceforge.net/)
[http://www.sgvlug.org/presentations/LinuxWeatherStation/index.html](http://www.sgvlug.org/presentations/LinuxWeatherStation/index.html)
[http://www.joejaworski.com/weather/](http://www.joejaworski.com/weather/)
[http://www.thunderheadtech.com/](http://www.thunderheadtech.com/)
[http://www.wviewweather.com/](http://www.wviewweather.com/)
[http://www.davisnet.com/weather/index.asp](http://www.davisnet.com/weather/index.asp)
[http://www.lacrossetechnology.com/](http://www.lacrossetechnology.com/)
[http://www.lavrsen.dk/twiki/bin/view/Open2300/WebHome](http://www.lavrsen.dk/twiki/bin/view/Open2300/WebHome)
[http://en.wikipedia.org/wiki/Personal_weather_station](http://en.wikipedia.org/wiki/Personal_weather_station)

---

### Post by sallymc on 2010-05-09
> **mikazo said:**
> After some searching, I did find a temperature module.

[http://www.alliedelec.com/Search/ProductDetail.aspx?SKU=6710082&MPN=DS1620&R=6710082&SEARCH=6710082&DESC=DS1620](http://www.alliedelec.com/Search/ProductDetail.aspx?SKU=6710082&MPN=DS1620&R=6710082&SEARCH=6710082&DESC=DS1620)

I've also come up with an idea for my own home-made anemometer. I'll most likely do a write-up on my blog if/when I finish the project.

Any news on your home-made anemometer - I see this was written nearly 2 years ago!  
Looking forward to hearing.  :)

---

### Post by mikazo on 2010-05-09
Sadly, the project fell by the wayside for me. It was a summer project while I was home from university for the summer, but it's been sitting in my parents' basement since then. Hopefully I can pick it up again one day when I have more room than an apartment to work on stuff.

If anyone else is working on a similar project, I'd still like to hear about it though.

---

### Post by Erlander on 2010-05-31
I have become interested in this topic too.

After lots of Google I found this.

[http://www.wviewweather.com/](http://www.wviewweather.com/)

It looks hopeful and even has a Debian?ubuntu repository.

Rob

---

