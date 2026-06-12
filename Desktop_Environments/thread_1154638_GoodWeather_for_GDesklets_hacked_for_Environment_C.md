---
title: "GoodWeather for GDesklets hacked for Environment Canada weather feeds"
date: 2009-05-10
forum: Desktop Environments
---

### Post by Emilie on 2009-05-10
Hello,

I just spent all day hacking the the GoodWeather gdesklet so that it uses Environment Canada for its weather feeds.  

[Download it Here (Gdesklets Site)]("http://www.gdesklets.de/index.php?q=desklet/view/240").  See the ReadMe in the Displays directory for more information and for finding your location code.

This includes a manually mapping of the environment canada "Conditions" and "Brief Descriptions" to the weather icons in GoodWeather (sorry not to the official environment canada ones).  This could be useful for someone who needs these mapping for another project.

Enjoy!

---

### Post by Emilie on 2009-06-27
Updated to use the new environment canada xml location.

---

### Post by tomcatacec on 2009-08-31
When the detail information is too long, GUI will have a problem.

It's better to truncate the detail information:
 
/usr/share/gdesklets/Sensors/GoodWeather# diff __init__.py.orig __init__.py
956c956
< 		today.details(details);
---
> 		today.details(details[0:100]);
1045c1045
< 			forecast.details(details);
---
> 			forecast.details(details[0:100]);

---

### Post by kapn on 2010-02-08
For those who may be struggling to get the right codes, the location listed in the INSTALL file is no longer available.  I have found them at:

[http://dd.weatheroffice.ec.gc.ca/citypage_weather/xml/siteList.xml](http://dd.weatheroffice.ec.gc.ca/citypage_weather/xml/siteList.xml)

---

### Post by kapn on 2010-02-08
And for the very lazy who may live in Toronto, the code for TO is ON/s0000458

---

### Post by Clutchface on 2011-04-24
Thanks guys!

But the site is asking for a user name & password??







--------------------------------------------

<site code="s0000788"><nameEn>Regina</nameEn><nameFr>Regina</nameFr><provinceCode>SK</provinceCode>

---

### Post by Emilie on 2011-04-25
It looks like it's something with the gdesklets site.  If you go to the base site (gdesklets.de) you can access it.

Or [click this link here!]("http://gdesklets.de/?q=desklet/view/240")

---

