---
title: "Xfce &quot;Weather Update&quot; plugin very inaccurate. Any alternatives?"
date: 2013-05-22
forum: Desktop Environments
---

### Post by postt on 2013-05-22
I added xfce "Weather Update" to my panel using Settings Manager > Panel > Items > Add New Items. 

The problem is the data of "Weather Update" is very inaccurate. Right now it's 60 degrees outside but "Weather Update" is showing 73 degrees.

Where does the weather data come from? Any ways to change the source of data to something more reliable? Or are there any alternative weather plugins I can put on the xfce panel?

Thanks.

---

### Post by Toz on 2013-05-22
You can configure the source by right-clicking on the plugin and selecting "Properties". More info [here]("http://goodies.xfce.org/projects/panel-plugins/xfce4-weather-plugin").

---

### Post by postt on 2013-05-22
> **Toz said:**
> You can configure the source by right-clicking on the plugin and selecting "Properties". More info [here]("http://goodies.xfce.org/projects/panel-plugins/xfce4-weather-plugin").

I went through that but didn't see any way to change the data source. Can you tell me how?

---

### Post by Toz on 2013-05-22
Right-click, Properties and change "Location Name" to your location. To to do so, click the "Change" button and search for your location. Is this what you mean?

---

### Post by postt on 2013-05-23
> **Toz said:**
> Right-click, Properties and change "Location Name" to your location. To to do so, click the "Change" button and search for your location. Is this what you mean?

No. My location is fine, I don't want to change that.

The problem is the weather data is completely inaccurate. The app says:

"Weather and astronomical data from		The Norwegian Meteorological Institute"

That's the problem. I'm in US so no wonder the weather data about my location coming all the from Norway is not accurate. I want to change the source of the weather data.

---

### Post by Toz on 2013-05-23
Oh. Sorry, but the weather source is hard-coded in the application. What is your location that the weather info is incorrect (if you don't mind sharing)? In my experience, the info from yr.no is pretty accurate.

---

### Post by zombifier25 on 2013-05-23
There's no weather source more accurate than your window.

Ok, let's be serious, weather info is never accurate. It's pretty hit and miss, and it's usually only correct 50% of the time. Personally, I use weather widgets for the looks only.

---

### Post by redhorse on 2013-05-27
I'm having the same problem, but I think those offering help don't quite understand.  The problem is with the reporting of current temperature and conditions, NOT the forecast.  I work in Arlington Heights, Illinois, USA, close to the Chicago Executive Airport (PWK).  In Xubuntu 12.04, the weather app pulled data from the local airports, so the current temperature and conditions were always perfectly reported.  In 13.04 the temperature is off by 5F to 10F most of the time, though on some rare occasions it comes to within 1F.  The other problem is that the conditions are frequently misreported, such as when the app reports that it is overcast and raining, but in reality the sky is blue and the sun is shining brightly (right now at 0400 UTC it reports that it is raining, but it is only overcast and dry).

At first, I thought my coordinates and altitude might have been incorrect.  So, I verified the information from multiple sources and input the data directly.  It actually made things a little worse.  Next, I put in the coordinates for the Chicago Executive Airport , which is the site of a NOAA weather station used by aviation.  This made things way worse.  I'm not sure where the Norwegian Meteorological Institute is getting their data from for my area, but something is clearly very wrong, either in the way the geographical coordinates are handled, or in the Norwegian Meteorological Institute's data sources.

If anyone wants to verify this for my specific location:
* In the Xubuntu weather app, enter "Arlington Heights, Illinois" for the location (default values from app: latitude 42.081268, longitude -87.980066, altitude 696 feet)
* On the web, go to [http://forecast.weather.gov/MapClick.php?textField1=42.1139&textField2=-87.9015&site=EAX]("http://forecast.weather.gov/MapClick.php?textField1=42.1139&textField2=-87.9015&site=EAX") - this is the Chicago Executive Airport weather station, about 3 miles straight east from my office over very flat terrain, so the weather is essentially the same.  The current conditions are in the first major section of the page.  This is what the Xubuntu 12.04 app used to get its data.

At the moment temperatures are close, but tomorrow when it warms up significantly, you should see a divergence.

---

### Post by Toz on 2013-05-28
A couple of points:

1. The weather plugin used to use The Weather Channel as its source. Unfortunately, back in 2011, The Weather Network changed from a free service to a paid subscription service. As a result, the Xfce developer's needed to look for another free source of weather data. They choose yr.no as the alternative. Some history is available in [this]("https://bugzilla.xfce.org/show_bug.cgi?id=8105") bug report.

2. When comparing the data, check the times for when the data was collected and compared. Earlier this morning, I noticed a difference in the weather conditions for Arlington Heights between the two sources, but there was also a 2 hour difference between the actual collection/reporting times. Perhaps this may have something to do with the discrepancy?

If the discrepancies continue, you can always create a bug report at [https://bugzilla.xfce.org/]("https://bugzilla.xfce.org/") to have the developer's look at the issue.

---

### Post by sudodus on 2013-05-28
I think a local or regional weather forecast is much more interesting than this 'current weather' plugin. The weather forecast usually needs more resources (for example a web browser), but gives you much more than what you see looking out from a window with a thermometer. There are also light versions of weather forecasts aimed at mobile phones.

But a weather plugin can give a crude notion of the weather at other places, which is nice.

---

### Post by Buntu Bunny on 2013-05-28
I always figured it was accurate for where the the station is located (in my case the airport on the other side of the county). Because of that I don't expect it to be accurate for my house. I only expect a ballpark. And, as Zombifier25 said, a weather widget sure does look neat.

---

