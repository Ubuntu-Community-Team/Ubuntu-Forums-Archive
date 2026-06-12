---
title: "Weather Report 2.30.0 applet update incorrect"
date: 2010-12-19
forum: Desktop Environments
---

### Post by 55tptag on 2010-12-19
Hello,

For the past month my "Weather Report 2.30.0 applet" is not indicating the correct weather under the tab "forecast".  See picture attached.

The applet has two tabs:
-Current conditions
-Forecast

The "forecast" tab has not updated for weeks.  For example, today is Sunday and as you can tell from the picture the "Forecast" tab still shows information for a Saturday from weeks ago.

Does anyone know how to fix this?

Thank you for your time and help.

---

### Post by 55tptag on 2010-12-22
this is also a problem I have with 10.10 when viewing New York weather.

---

### Post by Nimbus200 on 2010-12-22
That is strange.
I think it works on mine.
For New York, Kennedy Airport, it says 39F : Broken Clouds
What's yours?

Try changing the location to somewhere else, manually update it, then revert back to the location you want.

---

### Post by spottoid on 2010-12-22
I am having the same problem with the same set up - 10.04 and 2.30.0.  So, I switched to some town in Wyoming clicked the update button and current conditions went from 36 degrees to 50.  Then I went back to my local weather station, Teterboro, NJ and and current conditions went back to 36 and the forecast remained the same it says Wednesday's (today's) forecast followed by tomorrow's forecast Saturday.  It's been this way for about a month now.  Also, I've tried removing it from the top panel then reinstalling to no avail.  Any other suggestions?  Thanks.

---

### Post by Nimbus200 on 2010-12-23
Check your firewall or proxy ( if you're using one )
Make sure your firewall and proxy is allowing connection to weather.com

Have a look here :
[https://bugs.launchpad.net/ubuntu/+source/libsoup2.4/+bug/372647]("https://bugs.launchpad.net/ubuntu/+source/libsoup2.4/+bug/372647")

The workarounds there may solve yours

---

### Post by 55tptag on 2010-12-23
Thank you all for your feedback.  I did try changing the location and it seems to work for some other states but still not correct for NY State.

For example, today is Thursday and this is a partial listing of what the weather applet says as a New York Forecast (notice it skips any mention of Friday):
TODAY
MOSTLY CLOUDY. HIGHS IN THE MID 40S. NORTHWEST WINDS AROUND
10 MPH WITH GUSTS UP TO 25 MPH. 
    
TONIGHT
MOSTLY CLOUDY IN THE EVENING
THEN BECOMING PARTLY
CLOUDY. LOWS IN THE LOWER 30S. NORTHWEST WINDS 10 TO 15 MPH. 
  
SATURDAY
SUNNY AND BREEZY. HIGHS IN THE LOWER 40S. NORTHWEST
WINDS 15 TO 20 MPH WITH GUSTS UP TO 30 MPH. 

---
So, like I said I changed the state to test it.  And this is what is says as a forecast for Niagara Falls (notice that since today is Thursday that it includes Friday and it mentions Christmas):
REST OF TODAY
CLOUDY WITH SCATTERED SNOW SHOWERS. NEAR STEADY
TEMPERATURES IN THE MID 20S. NORTHWEST WINDS 10 TO 20 MPH. CHANCE OF
SNOW 50 PERCENT. 
  
TONIGHT
MOSTLY CLOUDY. LOWS IN THE LOWER 20S. NORTHWEST WINDS
10 TO 15 MPH. 
    
FRIDAY
MOSTLY CLOUDY IN THE MORNING
THEN BECOMING PARTLY SUNNY.
HIGHS IN THE UPPER 20S. NORTHWEST WINDS 10 TO 15 MPH. 
    
FRIDAY NIGHT
MOSTLY CLOUDY. LOWS 15 TO 20. NORTHWEST WINDS 10 MPH
OR LESS
BECOMING NORTH. 
  
CHRISTMAS DAY
MOSTLY CLOUDY. HIGHS IN THE MID 20S. NORTH WINDS
10 MPH OR LESS. 
  
SATURDAY NIGHT
MOSTLY CLOUDY WITH A 30 PERCENT CHANCE OF SNOW
SHOWERS. LOWS 15 TO 20. 

---
Then when I changed it back to NY it's incorrect and shows what it's been showing for the last month or so.  As I said today is Thursday and the forecast doesn't mention Friday:
TODAY
MOSTLY CLOUDY. HIGHS IN THE MID 40S. NORTHWEST WINDS AROUND
10 MPH WITH GUSTS UP TO 25 MPH. 
    
TONIGHT
MOSTLY CLOUDY IN THE EVENING
THEN BECOMING PARTLY
CLOUDY. LOWS IN THE LOWER 30S. NORTHWEST WINDS 10 TO 15 MPH. 
  
SATURDAY
SUNNY AND BREEZY. HIGHS IN THE LOWER 40S. NORTHWEST
WINDS 15 TO 20 MPH WITH GUSTS UP TO 30 MPH.

---

### Post by Nimbus200 on 2010-12-26
Well...Try using weather-util package.

```

sudo apt-get install weather-util

```

then try to get information about weather in a specific area using it.

```

weather-util --city="New York" --id KRDU

```

Other alternative is using Conky with weather script included.

---

### Post by ralfowen on 2010-12-26
i have same proplem  how  ican fixt

---

### Post by ricochen on 2011-01-30
Hi I have exactly the same problem. I think the data feed has problem. Could someone please take a look?

Ubuntu version: 10.10
Location: Farmingdale (NY)
Forecast:
TODAY ( --> Sunday )
MOSTLY CLOUDY. HIGHS IN THE MID 40S. NORTHWEST WINDS 5 TO
10 MPH WITH GUSTS UP TO 20 MPH. 
    
TONIGHT
MOSTLY CLOUDY IN THE EVENING
THEN BECOMING PARTLY
CLOUDY. LOWS IN THE LOWER 30S. NORTHWEST WINDS 10 TO 15 MPH. 
  
**SATURDAY ( this is tomorrow? doesn't make sense )**
SUNNY AND BREEZY. HIGHS IN THE LOWER 40S. NORTHWEST
WINDS 15 TO 20 MPH. 
    
SATURDAY NIGHT
PARTLY CLOUDY IN THE EVENING
THEN BECOMING
MOSTLY CLOUDY. LOWS IN THE UPPER 20S. NORTHWEST WINDS AROUND 15 MPH
WITH GUSTS UP TO 25 MPH. 
    
SUNDAY
PARTLY SUNNY IN THE MORNING
THEN BECOMING MOSTLY CLOUDY.
BREEZY WITH HIGHS IN THE UPPER 30S. NORTHWEST WINDS 15 TO 20 MPH. 
  
SUNDAY NIGHT
MOSTLY CLOUDY. LOWS AROUND 30. 
  
MONDAY
MOSTLY CLOUDY AND BREEZY. HIGHS IN THE AROUND 40. 
  
MONDAY NIGHT
MOSTLY CLOUDY AND BREEZY. LOWS AROUND 30. 
  
TUESDAY
PARTLY SUNNY AND WINDY. HIGHS AROUND 40. 
  
TUESDAY NIGHT
MOSTLY CLOUDY AND BREEZY. LOWS IN THE UPPER 20S. 
  
WEDNESDAY
PARTLY SUNNY AND BREEZY. HIGHS IN THE UPPER 30S. 
  
WEDNESDAY NIGHT
PARTLY CLOUDY. LOWS IN THE UPPER 20S. 
  
THURSDAY
MOSTLY SUNNY AND BREEZY. HIGHS IN THE UPPER 30S.

---

### Post by spottoid on 2011-02-05
cliffliang has it right in his post at [http://ubuntuforums.org/showthread.php?t=1648601](http://ubuntuforums.org/showthread.php?t=1648601).  All you have to do is figure out what your zone number was changed to, open /usr/share/libgweather/Locations.xml with vim and change your old (non-functioning) zone number to the new one.  Remember,  your zone number may be in two places (or three?) that are not near each other in the list and both have to be changed.  Hint:  Using the vim search function for your old zone number will ease eye strain.

---

### Post by 55tptag on 2011-02-05
thanks for finding the fix!
the bug with the fix is noted at: [https://bugzilla.gnome.org/show_bug.cgi?id=637597]("https://bugzilla.gnome.org/show_bug.cgi?id=637597")

---

### Post by roguejedi on 2011-12-24
i was able to correct this issue by going into synaptic package manager and selecting gnome-applets, marking for re-install with all upgrades. i installed and rebooted and weather report is back up and running

---

