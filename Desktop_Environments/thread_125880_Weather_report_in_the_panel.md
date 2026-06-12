---
title: "Weather report in the panel"
date: 2006-02-05
forum: Desktop Environments
---

### Post by Garyu on 2006-02-05
I added the Weather report to my panel. Not so beautiful, but IMO more accurate and informative than the desklets I've tried. However, I can't get a radar map for my city (Umeå, Sweden).

I tried going to weather.com from the button below the Radar map and search for Umea, Sweden and found this page with a radar image:
[http://www.weather.com/outlook/travel/businesstraveler/map/SWXX0038](http://www.weather.com/outlook/travel/businesstraveler/map/SWXX0038)

So now I know that the radar map exists on weather.com, but it still won't show in the Weather report thing. Not that it is that important, but it would be a nice feature to have it working. So, is there something I can edit to make this work? I don't even know where the panel apps are installed...

---

### Post by ronmarley1 on 2006-02-05
Hi Garyu,
I play aound a bit, and found this worked.  Right click on the applet icon and choose Preferences.  At the bottom of the General tab, click the box in front of "Use custom address for radar map."  Instead of putting in the URL for the page where the map is, I put in the address for the image that is displayed, for you, it would be [http://image.weather.com/images/sat/europesat_600x405.jpg](http://image.weather.com/images/sat/europesat_600x405.jpg).  (I got the address for the image from right clicking on it and choosing "Copy image location."  Hope this helps.  By the way, -11 Fahrenheit is quite cold!  It's a balmy 28 F here in Cleveland, Ohio, USA.

---

### Post by Garyu on 2006-02-05
[QUOTE=ronmarley1]Hi Garyu,
I play aound a bit, and found this worked.  [/QUOTE]

Alright! Heh, so easy, I should have been able to figure that one out... Oh well, I really appreciate the help. :)

-11 deg F really isn't that cold by Swedish standards though. :cool:

---

### Post by ronmarley1 on 2006-02-05
Anytime!  Glad I could help.

---

### Post by Old Jimma on 2007-07-13
Y'all

Ron Marley is right. If you choose a weather station (by right click > preferences > location on the weather panel applet, it is possible that weather.com does not have a radar map for that specific location.

For example, I live in the US, nearby Atlanta but want the weather from the nearest NOAA weather station in Lawrenceville, GA.

When I choose Lawrenceville, GA as my location, the weather applet doesn't find a radar map for it automatically... it is up to you to tell the applet what radar or satalite map you want. When you find one from weather.com or noaa.gov you must right click on the map and "copy link location." Test the location by pasting it into your browser's address box. Is it a .jpg file? In my experience if it is not a .jpg file, then the weather applet won't like it.

For example, I like the national weather satelite .jpg at [http://www.goes.noaa.gov/ECIR4.html]("http://www.goes.noaa.gov/ECIR4.html")... the image there is the national satelite photo and has the URL [http://www.goes.noaa.gov/GIFS/ECI8.JPG]("http://www.goes.noaa.gov/GIFS/ECI8.JPG"). This latter URL can be pasted into the weather applet at the appropriate spot.

On the other hand, if you want the weather.com radar satelite of a location close to you, that is possible, also ... but I think those maps look pretty clunky compared to noaa maps. For example,a decent weather map of the SE US is [http://image.weather.com/images/maps/current/cur_se_720x486.jpg]("http://image.weather.com/images/maps/current/cur_se_720x486.jpg")

Mouse arround the weather URLs and you'll find the jpg images you want. Be patient.

Thank you Ubuntu community!

Phil Smith
Duluth, GA

---

### Post by Old Jimma on 2007-07-13
Oh, yes.. one last important comment...

After you paste the jpg url into the weather panel applet, it will not take effect immediately. You either must wait for the applet to update its weather info, or restart your computer... then you'll see the map you want!

Best regards,
Phil Smith
Duluth, Ga

---

### Post by Old Jimma on 2007-07-16
Hi Folks:

I tested using gif files as the URL for weather maps... that works, also!

eg., [http://www.hpc.ncep.noaa.gov/noaa/noaa.gif]("http://www.hpc.ncep.noaa.gov/noaa/noaa.gif") works nicely!!

Phil Smith
Duluth, GA

---

### Post by Skidpad on 2007-07-16
Great info guys!  I just installed the weather "applet" yesterday, but hadn't tried the radar image yet.  This thread got me up & running right away.

Another tip o' the hat to the Ubuntu community!

---

### Post by djxcon on 2007-07-19
Thanks for the help gang!  On weather.com I used my zip code and then chose the radar option.  Next I had to click on the link for "Original Radar Map."  This next page displayed another radar in which I could right click on and choose Copy Image Location.  After pasting this location into the address for the weather applet radar location, I was able to update the Radar Map.

---

### Post by Old Jimma on 2007-07-20
Glad it worked!!

Phil Smith
Duluth, GA

---

