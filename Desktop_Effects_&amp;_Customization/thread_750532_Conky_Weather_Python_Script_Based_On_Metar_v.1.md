---
title: "Conky Weather Python Script Based On Metar v.1"
date: 2008-04-09
forum: Desktop Effects &amp; Customization
---

### Post by kaivalagi on 2008-04-09
Hi All,

[B][COLOR="Blue"]New script posted in new thread
[URL="http://ubuntuforums.org/showthread.php?p=4752373"]http://ubuntuforums.org/showthread.php?p=4752373
[/URL]
I'll keep an eye on this thread for a while, but I don't really want to support anything too old so please use the new script on the new thread wherever possible
Thanks[/COLOR][/B]

I have just put together a python script to produce various bits of weather data on demand for use in Conky. This sort of thing has been done already by lvleph, a post for his contribution is [here]("http://ubuntuforums.org/showthread.php?t=666842"). 

I wanted to create something, firstly to gain some experience with Python, and secondly so that there was no dependency on the yahoo weather website and it's formatting. This hopefully means that it will have a little longevity.

Currently the script does not provide forecasted weather, only the current weather last recorded at a weather station. It would be nice to have forecasted weather but I make no promises, maybe my next attempt will be based on the google app engine...if it can provide weather data.... I suggest using the script created by lvleph linked above if you want forecast info :) **[COLOR="Red"]EDIT: I have added a forecasting python script lower down in the thread, it is no longer based on PyMetar, it uses the weather.com xoap service instead, see it  [here]("http://ubuntuforums.org/showpost.php?p=4708045&postcount=10")[/COLOR]** 

I have used the PyMetar python module to access NOAA weather data for anywhere in the world (I think), and have set it up to cache the data from a call,unless an expiry is reached (so it doesn't hit the internet on each call). Detail on PyMetar can be found [here]("http://www.schwarzvogel.de/software-pymetar.shtml")

So, please have a play with it, let me know what you all think, and tell me if I need to elaborate more on the setup process etc etc. Any suggestions to improve it are welcome, whether it be the code or usage.

Hope some of you find it useful


**[SIZE="3"]Steps To Get It Working[/SIZE]**

**Step 1:** Ensure you have the package dependencies such as python and pymetar:

```
sudo apt-get install python
sudo apt-get install python-pymetar
```

**Step 2:** Install the attached weather font, by extracting the ttf to your desktop, then doing the following (copy and register):

```
cp ~/Desktop/weather.ttf ~/.fonts/ && fc-cache -f -v
```

If you don't have a .fonts folder create one:

```
mkdir ~/.fonts
```

**Step 3:** Save the attached script called conkyGlobalWeather.py.txt as ~/.scripts/conkyGlobalWeather.py for example (lose the .txt) and make sure is executable:

```
chmod a+x ~/.scripts/conkyGlobalWeather.py
```

**Step 4:** Use the attached conkyrc-GlobalWeather.txt file to test and/or create your own conky config:

```
conky -c ~/Desktop/conkyrc-GlobalWeather.txt
```


**[SIZE="3"]Example Usage[/SIZE]**

An example in a conky config of the retrieval of the current conditions for Norwich, UK is below. Note the first argument passed to the script, it is the station reference, to find yours go to [http://www.nws.noaa.gov/tg/siteloc.shtml]("http://www.nws.noaa.gov/tg/siteloc.shtml")

```
${execi 3600 python ~/.scripts/conkyGlobalWeather.py EGSH M I I C}
```

If you wanted a nice weather font based output you would do something like this:

```
${font Weather:size=36}${execi 3600 python ~/.scripts/conkyGlobalWeather.py EGSH M I I F}${font}
```

The usage of the script is detailed below and can also found in the script for reference. 

```
 Usage: conkyGlobalWeather.py StnRef TempUnit WindUnit VisUnit DataType

     Where StnRef:   e.g. EGSH -> http://www.nws.noaa.gov/tg/siteloc.shtml

           TempUnit: M = Metric (°C)
                     I = Imperial (°F)

           WindUnit: M = Metric (m/s)
                     K = Metric (kph)
                     I = Imperial(mph)

           VisUnit:  M = Metric (kilometers)
                     I = Imperial (miles)

           DataType: T = Temperature
                     W = Wind
                     V = Visibility
                     S = StationName
                     D = Description
                     C = Conditions
                     H = Humidity
                     F = Weather Font Character (Based on Pixmap)

                     Note: Only one data type should be given at any time
```


**[SIZE="3"]Script Constants[/SIZE]**

The following constants are worth a mention, you can adjust these in the script to change the default cache file location, the width of textual wrapping, when it occurs, and the expiry in minutes before a new set of data is grabbed off the net.

```
TEMP_FILEPATH="/tmp/globalweather.pkl"
WRAP_WIDTH = 40
EXPIRY_MINUTES = 90
```

---

### Post by martynp on 2008-04-10
Can't believe no one has replied to this yet.

The script I was using by Ivleph seemed to stop working the other day and it prompted me to fine down my Conky script (as the new version of Screenlets actually is very good).

Anyway... saw yours this morning and got it working in a flash so well happy.

I have attached a screenie to show how I have rearranged it slightly. No need to attach the script I think as it is only basic conky formatting.

Great job and I really hope you can find a way of getting the forecasts too!

Thanks,

Martyn

---

### Post by SomeGuyDude on 2008-04-10
Huzzah!! Everything's just how I wanted it. I even tweaked the formatting a little and didn't break it. EXCELLENT.

I suppose the lack of "forecast" is a problem for most, but I just need current conditions, so it's got everything I need already.

---

### Post by kaivalagi on 2008-04-10
For info, I have a couple of options to mess around with for forecasting data, which I've tracked down.

1) The Yahoo weather rss feed, equivalent to where lvleph sourced his data from but in rss/xml format.

2) The NDFD XML webservice, but I get the feeling it is only for the US...I need to check it out properly. Details here [http://www.weather.gov/xml/]("http://www.weather.gov/xml/"). I would prefer this approach if feasible for global weather as the level of detail obtainable is really high I think, and it's a web service which is cool.

3) The google weather api, which returns xml for a city name. This could be hard to resolve all locations people need to use it for, so I probably won't use this.

There are no api's available in the google app engine...yet. Early days.

I do have to give it a rest for a few days (the wife is getting pissed off with me spending all my time on Linux :) ), once I'm in the good books I'll give it a crack...it shouldn't take long cause I've done all the ground for web service handling using SOAPPy and fetching and interpreting xml from rss feeds using the minidom and urllib2 :)

Anyone know of any other web service / xml services I can use to source global weather forecasts...? I want to know of all the alternatives before I pick one,cause I don't want to change again.

Also I will be attempting to object orientate the solution later on too 'cause this is an exercise for me to learn the Python language and support libraries after all :)

---

### Post by martynp on 2008-04-10
Thanks for the reply and I look forward to further updates.... (I understand about the wife thing mate... lol)

I have always found the forecasts from weather.com to be pretty reliable for the UK but don't know if they are accessible.

Thanks again for the great work!

Martyn

---

### Post by SomeGuyDude on 2008-04-10
All that matters to me is I still have current conditions in the right format, complete with the little degree symbol (I needed that!). Take your time on the rest!

---

### Post by kaivalagi on 2008-04-10
I just hit the jackpot, I love open source!

I think I will be using some of the python code from the awn weather applet, which uses the weather.com xml feed for forecasting data. All the xml extraction is done for me, all thanks to Mike (mosburger) Desjardins, the author, thanks Mike! :KS Just a bit of retro fitting in order and I'll be there.

If you use AWN I highly recommend his applet, it even provides a satellite weather map of your location.

Anyway, I'll post a new install guide here when it's done :) Shouldn't be more than a week, wife permitting...

Cheers

---

### Post by Bruce M. on 2008-04-12
Hi folks,

[CENTER][[IMG]http://img399.imageshack.us/img399/6281/weatherpysw5.th.jpg[/IMG]](http://img399.imageshack.us/my.php?image=weatherpysw5.jpg)
[/CENTER]

Any ideas why this isn't working?

Spacer?
When "spacer yes" didn't work I set it to "spacer right", when that produced the same error I commented it out:
```

# conky configuration
# edited by kaivalagi

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Terminus:size=9

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 300 5
maximum_width 300

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# own window options
own_window		yes
own_window_transparent	yes
own_window_type		override
own_window_hints	undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 0

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
# use_spacer right

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT



 Station Name: ${execi 3600 python ~/scripts/conkyGlobalWeather.py EGSH M I I S}
 Conditions: ${execi 3600 python ~/scripts/conkyGlobalWeather.py EGSH M I I C}
 Description: ${execi 3600 python ~/scripts/conkyGlobalWeather.py EGSH M I I D}
 ${font Weather:size=36}${execi 3600 python ~/scripts/conkyGlobalWeather.py EGSH M I I F}${font}
 Temperature: ${execi 3600 python ~/scripts/conkyGlobalWeather.py EGSH M I I T}
 Wind: ${execi 3600 python ~/scripts/conkyGlobalWeather.py EGSH M I I W}
 Visibility: ${execi 3600 python ~/scripts/conkyGlobalWeather.py EGSH M I I V}
 Humidity: ${execi 3600 python ~/scripts/conkyGlobalWeather.py EGSH M I I H}

```

---

### Post by kaivalagi on 2008-04-12
> **Bruce M. said:**
> Hi folks,

[CENTER][[IMG]http://img399.imageshack.us/img399/6281/weatherpysw5.th.jpg[/IMG]](http://img399.imageshack.us/my.php?image=weatherpysw5.jpg)
[/CENTER]

Any ideas why this isn't working?

Hi Bruce, I am currently testing my conky scripts etc in Gutsy with conky 1.49, and I guess you're using Hardy and/or a newer conky version, due to the spacer option difference?

I would suggest for now that you take the TEXT part of the test config and paste that into a known working script of your own to try things out...

I'll be making the switch to Hardy for my main OS when it's out of beta end of the month, I only have it on a test partition for now and don't boot into it very often.....

Sorry I can't be of more help

---

### Post by kaivalagi on 2008-04-13
I have a working python script with forecasting, see conkyForecast.py.txt attached. (you might what to remove the .txt)

Usage as follows:

```
 Usage: conkyForecast.py <Location Code> <Units> <Data Type> <Day Number>

     Where <Location Code>: Use the following url to determine your 
                            location code by city name:
                            http://xoap.weather.com/search/search?where=Norwich

                    <Unit>: M = Metric (e.g. °C)
                            I = Imperial (e.g. °F)

                <DataType>: DW - Day Of Week
                            WF - Weather Font Output
                            LT - Low Temp (current when today's conditions)
                            HT - High Temp (current when today's conditions)
                            CC - Current Conditions
                            CT - Conditions Text
                            PC - Precipitation Chance
                            HM - Humidity
                            WD - Wind Direction
                            WS - Wind Speed
                            WG - Wind Gusts
                            CN - City Name

                      Note: Only one data type should be given at any time

              <Day Number>: A number from 0 to 7 (0 = today, 7 = 7 days ahead)

```

Example conky config lines for today and tomorrow  based on above usage:

```
City Name: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M CN 0}

Day: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M DW 0}
Conditions: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M CC 0}
${font Weather:size=36}${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M WF 0}${font}
Temp: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M HT 0}
Wind: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M WS 0}
Humidity: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M HM 0}

Day: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M DW 1}
Conditions: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M CC 1}
${font Weather:size=36}${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M WF 1}${font}
High Temp: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M HT 1}
Low Temp: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M LT 1}
Wind: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M WS 1}
Humidity: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M HM 1}
Precipitation: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M PC 1}
```


If anyone can get together a conky config which uses the above to display several days forecasting nicely, and post it here, that would be great.

Any issues post back and I'll try to answer/fix ASAP. ANy suggestions for improvement are always welcome :)

Cheers

---

### Post by Bruce M. on 2008-04-13
> **kaivalagi said:**
> Hi Bruce, I am currently testing my conky scripts etc in Gutsy with conky 1.49, and I guess you're using Hardy and/or a newer conky version, due to the spacer option difference?

[CENTER]**My secret is out!**[/CENTER]

I'm a dyed in the wool non-beta tester. However, saying that, there is one program (in Linux) that I will beta test for anytime, QuickStart  (see my sig), because I believe in it with out question.  :)

Because of that trust I decided to "upgrade" to 8.04 and if it didn't work I knew QS would get me back to 7.10 painlessly.

> **kaivalagi said:**
> I would suggest for now that you take the TEXT part of the test config and paste that into a known working script of your own to try things out...

OK, I did that an got partial results.  Guess I'll be "beta" testing this in HH for you until it's out officially, because for all other purposes it is working here.

> **kaivalagi said:**
> I'll be making the switch to Hardy for my main OS when it's out of beta end of the month, I only have it on a test partition for now and don't boot into it very often.....

Sorry I can't be of more help

But maybe someone else can.  :)
Here's my screen shot after putting the text portion into a known working conky file. All I did was change the location to SABA (Buenos Aires) and made it align top left.

[CENTER]
[[IMG]http://img237.imageshack.us/img237/2482/weatherpy2ur6.th.jpg[/IMG]](http://img237.imageshack.us/my.php?image=weatherpy2ur6.jpg)
[/CENTER]
```

Meteorological Station Information Lookup
for SABA

      WMO Index Number: 	87585
      ICAO Location Indicator: 	SABA
      Station Name: 	Buenos Aires Observatorio
      Country: 	Argentina
      WMO Region: 	3
      Station Position: 	34-35S    058-29W (dms)
      Station Elevation (Ha): 	25 Meters
      Upper Air Elevation (Hp): 	25 Meters
```


As you see, I get some stuff, not all, maybe I need to change SABA to the other local for BsAS: The Airport. I saw it but didn't save the info. Don't know if that will work but I'll try that later today to see.

Here is what is in my terminal:

```

Sun Apr 13 at: 13:47:53 
bruloo @ ~  $ Conky: desktop window (120005d) is subwindow of root window (46)
Conky: window type - override
Conky: drawing to created window (2c00001)
Conky: drawing to double buffer
Conky: desktop window (120005d) is subwindow of root window (46)
Conky: window type - override
Conky: drawing to created window (2600001)
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 226, in <module>
    pr = FetchData(StnRef)
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 139, in FetchData
    re = rf.FetchReport()
  File "/var/lib/python-support/python2.5/pymetar.py", line 967, in FetchReport
    raise NetworkException, why
pymetar.NetworkException
Traceback (most recent call last):
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 226, in <module>
    pr = FetchData(StnRef)
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 139, in FetchData
    re = rf.FetchReport()
  File "/var/lib/python-support/python2.5/pymetar.py", line 967, in FetchReport
    raise NetworkException, why
pymetar.NetworkException
Traceback (most recent call last):
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 226, in <module>
    pr = FetchData(StnRef)
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 139, in FetchData
    re = rf.FetchReport()
  File "/var/lib/python-support/python2.5/pymetar.py", line 967, in FetchReport
    raise NetworkException, why
pymetar.NetworkException
Traceback (most recent call last):
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 226, in <module>
    pr = FetchData(StnRef)
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 139, in FetchData
    re = rf.FetchReport()
  File "/var/lib/python-support/python2.5/pymetar.py", line 967, in FetchReport
    raise NetworkException, why
pymetar.NetworkException
Traceback (most recent call last):
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 226, in <module>
    pr = FetchData(StnRef)
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 139, in FetchData
    re = rf.FetchReport()
  File "/var/lib/python-support/python2.5/pymetar.py", line 967, in FetchReport
    raise NetworkException, why
pymetar.NetworkException
Traceback (most recent call last):
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 226, in <module>
    pr = FetchData(StnRef)
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 139, in FetchData
    re = rf.FetchReport()
  File "/var/lib/python-support/python2.5/pymetar.py", line 967, in FetchReport
    raise NetworkException, why
pymetar.NetworkException
Traceback (most recent call last):
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 226, in <module>
    pr = FetchData(StnRef)
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 139, in FetchData
    re = rf.FetchReport()
  File "/var/lib/python-support/python2.5/pymetar.py", line 967, in FetchReport
    raise NetworkException, why
pymetar.NetworkException
Traceback (most recent call last):
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 226, in <module>
    pr = FetchData(StnRef)
  File "/home/bruloo/scripts/conkyGlobalWeather.py", line 139, in FetchData
    re = rf.FetchReport()
  File "/var/lib/python-support/python2.5/pymetar.py", line 967, in FetchReport
    raise NetworkException, why
pymetar.NetworkException
bruloo @ ~  $ 

```

Does this mean there is going to be a major overhaul of the script when HH becomes official? And will the changes be backwards compatible?

So far it seems "conkys" spacer command is not backward compatible, I'll have to find the "new" command / variable page for that today too.

Have a Great Day
Bruce

**EDIT:**
1. Since I can't fine how to actually see that data on their website, maybe it's not the same format I don't know.
2. Have you looked at [Weather Underground]("http://www.wunderground.com/") as an alternative? Their "Terms of Service" are very favourable for this. Even to copying the information locally for personal use. And it gives a TON of information.

---

### Post by kaivalagi on 2008-04-13
> **Bruce M. said:**
> Does this mean there is going to be a major overhaul of the script when HH becomes official? And will the changes be backwards compatible?

The script works as is for any Linux distro that also has the PyMetar solution installed. Any problems that stem from the conky configuration are really down to the individual to get sorted. If there are any issues with the PyMetar aspect of the solution I can try to help out but  I am not the person who developed it so am only useful to a point.

I think the PyMetar issues you are having could relate to the site which hosts the data being a US based government agency.  Maybe they aren't so concerned with non-US weather...I haven't tried any other locations with it other than my own.

I had a look at the PyMetar script and it uses the following url to obtain the data:

```
http://weather.noaa.gov/pub/data/observations/metar/decoded/**StaRef**.TXT
where StaRef is the looked up value. 
``` Maybe the data you were requesting wasn't available when you tested it...not sure. The errors you were getting do seem to be because the website doesn't understand the station reference based URL PyMetar has requested.

I would suggest switches over to my newer script, a few posts back. it is based on weather.com, so  if you can see your weather forecasts on that site it will work for you.

> **Bruce M. said:**
> 
1. Since I can't fine how to actually see that data on their website, maybe it's not the same format I don't know.

Since the NOAA service is a data repository / web service and not a web site, there is no real frontend as you'll see with yahoo weather.

> **Bruce M. said:**
> 
2. Have you looked at [Weather Underground]("http://www.wunderground.com/") as an alternative? Their "Terms of Service" are very favourable for this. Even to copying the information locally for personal use. And it gives a TON of information.

I had a quick look at the weather underground site, and yes it has a bunch of details on it, but I couldn't find any nice way to obtain details other than scraping the web page content which is not what I want to do. If the web page design changes the script will break etc. Do you know of a webservice/xml feed from that website? If there is one to obtain the same data you can navigate to on the pages, then I can go with that, safe in the knowledge the script will remain in a working state for some time.

I really really want to limit these scripts I am knocking together to using xml feeds or web services as these are built for the purpose of providing data like this.  Have you tried out my newer script above based on the weather.com xoap service, I found the following compatible locations for forecast data that may interest you:

```
  <loc id="ARDF0127" type="1">Aeroparque Buenos Aires, Argentina</loc>
  <loc id="ARBA0009" type="1">Buenos Aires, Argentina</loc>

```

If you setup the conkyForecast.py script using a location_code of ARBA0009 you should be good...

I suggest you give my newer script a try. As I said it's based on the weather.com site and is already used by the AWN Weather applet. I could even embed a satellite picture of the current weather if conky would allow it :)

I hope that helps

---

### Post by yousillygoose on 2008-04-13
Okay.  So this script uses many different exec's to to pull forecasting weather?  If I understand this correctly that would use much more processing and memory power with all of the commands.  Am I correct?

---

### Post by kaivalagi on 2008-04-13
> **yousillygoose said:**
> Okay.  So this script uses many different exec's to to pull forecasting weather?  If I understand this correctly that would use much more processing and memory power with all of the commands.  Am I correct?

It is more granular in nature than others, and does require more execi calls in a conky config to get the same amount of data.

However, the script shouldn't need to get called with that much frequency, so even though there might be a 'spike' in activity, it is only for a short time, and doesn't happen again until the execi is called again based on it's interval (which could be set to every 2 hours if wanted for example).

As for the web calls it makes, it will only make 2  trips to the web service to collect data for current and forecasted info, no matter what options you pass. Each attempt after that is checked against an expiry setting and a downloaded xml file. Currently the expiry is set to 90 minutes, this could be set to half a day if desired to reduce the interval of web calls per day too.

Yes, there is an argument that it will make more calls than some of the other scripts such as lvleph's, as his collects 5 days of forecast font characters in one trip for example. In theory the script could be made to do the same thing, it would just need to loop through a collection of day forecasts that are already present when it is instantiated, and return multiple parts of data. Rather than passing it "WF 0" for current weather font data for example, something like "WF 0-4" could be passed to bring back 5 days of info.

I don't really see the necessity for this though, unless it can be demonstrated that the script calls use too much memory and cpu to cause a system to suffer. If a change is truly needed then I can go about updating the script to handle more options like this. With todays average low spec systems (i.e. a few years old pentiums/amds or mini itx) this shouldn't need to be a consideration.

Fair enough?

---

### Post by Bruce M. on 2008-04-13
> **kaivalagi said:**
> I had a quick look at the weather underground site, and yes it has a bunch of details on it, but I couldn't find any nice way to obtain details other than scraping the web page content which is not what I want to do. If the web page design changes the script will break etc. Do you know of a webservice/xml feed from that website? If there is one to obtain the same data you can navigate to on the pages, then I can go with that, safe in the knowledge the script will remain in a working state for some time.

It has RSS Feed:
87582.xml = Buenos Aires

[http://rss.wunderground.com/auto/rss_full/global/stations/87582.xml?units=both](http://rss.wunderground.com/auto/rss_full/global/stations/87582.xml?units=both)

> **kaivalagi said:**
> I really really want to limit these scripts I am knocking together to using xml feeds or web services as these are built for the purpose of providing data like this.  Have you tried out my newer script above based on the weather.com xoap service, I found the following compatible locations for forecast data that may interest you:

```
  <loc id="ARDF0127" type="1">Aeroparque Buenos Aires, Argentina</loc>
  <loc id="ARBA0009" type="1">Buenos Aires, Argentina</loc>

```

If you setup the conkyForecast.py script using a location_code of ARBA0009 you should be good...

I suggest you give my newer script a try. As I said it's based on the weather.com site and is already used by the AWN Weather applet. I could even embed a satellite picture of the current weather if conky would allow it :)

I hope that helps

Used that code with lvleph's perl script and just tried it with yours. It works, but only for two days.

I also note that it will be easy to punch in Spanish for certain things. Like my image attachment shows the first change: Today = Hoy

So now my work is cut out, adding Spanish and formatting.  :)

Thanks ...
Bruce

---

### Post by kaivalagi on 2008-04-13
> **Bruce M. said:**
> It has RSS Feed:
Used that code with lvleph's perl script and just tried it with yours. It works, but only for two days.
Bruce

I looked at the xml content from the rss feed for wunderground and the content retrieved from it is summary data like this:

```
<item>



       <title>Buenos Aires, Argentina Current Conditions - 8:00 PM ART Apr. 13</title>    

        <link>http://www.wunderground.com/global/stations/87582.html</link>

	<description>Temperature: 52°F / 11°C | Humidity: 67% | Pressure: 30.04in / 1017hPa | Conditions: Clear | Wind Direction: SW | Wind Speed: 17mph / 28km/h | Updated: 8:00 PM ART

	</description>

        <pubDate>Sun, 13 Apr 2008 23:00:00 GMT</pubDate>

        <guid isPermaLink="false">1208127600</guid>

</item>
```

I guess this could be used but it is far from ideal. All the weather details are just text within the description tags. They could be split out easily though using "|" and ":"... Bottom line, I would sooner get the current script working properly than need to rewrite it for use with the wundergrand content.

If you visit the weather.com site do you get the same restriction in forecast data. I have the next week of forecast data for a UK location, I would assume it's the same for you...you need to read the usage text, if you use a 3/4/5 etc instead of 0 or 1 you will get more forecast data for the days ahead)
[COLOR="Red"]Edit[/COLOR]: I knocked up conky config for a few more days of forecasting, you can go up to day 7 if you'd like:
```
${color1}${font Weather:size=30}${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M WF 0}${font}     ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M CC 0} , Humidity:${execi 3600 python ~/Scripts/conky//conkyForecast.py UKXX0103 M HM 0}
  ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 0}

${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M DW 1}  ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M DW 2}  ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M DW 3}
${font Weather:size=32}${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M WF 1} ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M WF 2} ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M WF 3}${font}
  ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 1}         ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 2}         ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 3}
```


The translating of the language inside the script shouldn't be too hard by the way, the condition_text under the WeatherText class for example could be translated and used in conjunction with the CC option when needing it in Conky. If a new condition_text_es array was created based on this, the locale could be used to convert codes to Spanish instead of English...pass me the converted condition_text and I can have a crack at it (never used locales in Python before :) ). If you want to provide some translation I can incorporate it into the script, just let me know and I can pass on the list of condition test for translation.

> **Bruce M. said:**
> 
So now my work is cut out, adding Spanish and formatting. 


Try writing a script to suits everyone's needs ;)

---

### Post by Bruce M. on 2008-04-14
> **kaivalagi said:**
> I looked at the xml content from the rss feed for wunderground and the content retrieved from it is summary data like this:

```
<item>



       <title>Buenos Aires, Argentina Current Conditions - 8:00 PM ART Apr. 13</title>    

        <link>http://www.wunderground.com/global/stations/87582.html</link>

	<description>Temperature: 52°F / 11°C | Humidity: 67% | Pressure: 30.04in / 1017hPa | Conditions: Clear | Wind Direction: SW | Wind Speed: 17mph / 28km/h | Updated: 8:00 PM ART

	</description>

        <pubDate>Sun, 13 Apr 2008 23:00:00 GMT</pubDate>

        <guid isPermaLink="false">1208127600</guid>

</item>
```

I guess this could be used but it is far from ideal. All the weather details are just text within the description tags. They could be split out easily though using "|" and ":"... Bottom line, I would sooner get the current script working properly than need to rewrite it for use with the wundergrand content.

It's your script, and it's working again. At least until weather.com changes their format again. :)

> **kaivalagi said:**
> If you visit the weather.com site do you get the same restriction in forecast data. I have the next week of forecast data for a UK location, I would assume it's the same for you...you need to read the usage text, if you use a 3/4/5 etc instead of 0 or 1 you will get more forecast data for the days ahead)
[COLOR="Red"]Edit[/COLOR]: I knocked up conky config for a few more days of forecasting, you can go up to day 7 if you'd like:
```
${color1}${font Weather:size=30}${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M WF 0}${font}     ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M CC 0} , Humidity:${execi 3600 python ~/Scripts/conky//conkyForecast.py UKXX0103 M HM 0}
  ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 0}

${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M DW 1}  ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M DW 2}  ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M DW 3}
${font Weather:size=32}${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M WF 1} ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M WF 2} ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M WF 3}${font}
  ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 1}         ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 2}         ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 3}
```

Yes, but those execi codes are a killer on my 800MHtz 512MB Ram PC  :)

> **kaivalagi said:**
> The translating of the language inside the script shouldn't be too hard by the way, the condition_text under the WeatherText class for example could be translated and used in conjunction with the CC option when needing it in Conky. If a new condition_text_es array was created based on this, the locale could be used to convert codes to Spanish instead of English...pass me the converted condition_text and I can have a crack at it (never used locales in Python before :) ). If you want to provide some translation I can incorporate it into the script, just let me know and I can pass on the list of condition test for translation.

I've actually deleted three execi calls:
```

# City: ${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M CN 0}
# ${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M DW 0}
# Tofay: ${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M DW 1}
```
It's just as easy to type that info in.

Here is my **test** conky with your script and a screen shot with it working in my conky as well.

My test conky:
```

background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
use_xft yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 0.5
update_interval 5.0
draw_shades no
draw_outline yes  # amplifies text if yes
draw_borders no
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
alignment top_left  # top_right, top_left, bottom_left, bottom_right
gap_x 10
gap_y 35
no_buffers yes  # Subtract file system buffers from used memory?
draw_outline yes
draw_shades yes  # shadecolor black
default_outline_color black
default_shade_color black

# Desde: ${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M CN 0}
# ${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M DW 0}
# Día: ${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M DW 1}

TEXT
${color cyan}${hr 1} $color
${color lightblue}Desde:${color} Buenos Aires, Argentina
${voffset 5}${color lightblue}Lat: ${color orange}34°35'S  ${color lightblue}Long: ${color orange}58°21'W ${alignr} ${color lightblue}Alt: ${color orange}25 m$color
${color cyan}${hr 1}${color}
${color lightblue}Ahora: ${color orange}Condiciones: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M CC 0}
${font Weather:size=50}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WF 0}${font}
${font Zekton:size=20}${offset 50}${voffset -48}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HT 0}${font}${color}
${color lightblue}${voffset 10}Viento: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WS 0}${alignr 2}${color lightblue}Humedad: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HM 0}
${color cyan}${hr 1}$color
${color lightblue}Mañana: ${color orange}Condiciones: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M CC 1}
${offset 3}${font Weather:size=40}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WF 1}${font}
${color lightblue}${offset 35}${voffset -33}Max: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HT 1}  ${color lightblue}Min: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M LT 1}
${color lightblue}${voffset 10}Viento: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WS 1}${alignr 2}${color lightblue}Humedad: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HM 1}
${alignc}${color lightblue}Precipitaciones: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M PC 1}${color}
${color cyan}${hr 1}${color}

```
And the screenshot:

[CENTER]
[[IMG]http://img261.imageshack.us/img261/9328/screenshotyr8.th.jpg[/IMG]](http://img261.imageshack.us/my.php?image=screenshotyr8.jpg)
[/CENTER]

> **kaivalagi said:**
> Try writing a script to suits everyone's needs ;)

I can't program worth a plug nickel, but my logical mind lets me edit things I see.  :)

Translations coming soon, I have to eat now.

Also note: I'm back to Xubuntu 7.10, HH Gnome was way to slow and I had a few more problems that suggest Xfce is better on this old machine.  :)

Have a good evening.
Bruce

---

### Post by kaivalagi on 2008-04-15
> **Bruce M. said:**
> Yes, but those execi codes are a killer on my 800MHz 512MB Ram PC 

You got an eee pc/itx?

Do you thing there needs to be the ability to have a range of days setting for output?

i.e.

as well as this for a single day:
${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 1}

we have this to get back the next 5 days worth of something:
${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 1 5}

I could look out for the last day_number argument say, and if present bring back a range of data, if not there then just bring back the one piece, if that makes sense. I could do this for all the available data types.

Users will need to tweak spacer settings in the script then though, and not arrange output through the conky config anymore...

Thanks for all your constructive feedback! :)

---

### Post by yousillygoose on 2008-04-15
> **kaivalagi said:**
> You got an eee pc/itx?

Do you thing there needs to be the ability to have a range of days setting for output?

i.e.

as well as this for a single day:
${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 1}

we have this to get back the next 5 days worth of something:
${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 1 5}

I could look out for the last day_number argument say, and if present bring back a range of data, if not there then just bring back the one piece, if that makes sense. I could do this for all the available data types.

Users will need to tweak spacer settings in the script then though, and not arrange output through the conky config anymore...

Thanks for all your constructive feedback! :)

I would love to have this ability.  This is pretty much exactly what I am looking for  :)

---

### Post by yousillygoose on 2008-04-15
> **kaivalagi said:**
> I have a working python script with forecasting, see conkyForecast.py.txt attached. (you might what to remove the .txt)

Usage as follows:

```
 Usage: conkyForecast.py <Location Code> <Units> <Data Type> <Day Number>

     Where <Location Code>: Use the following url to determine your 
                            location code by city name:
                            http://xoap.weather.com/search/search?where=Norwich

                    <Unit>: M = Metric (e.g. °C)
                            I = Imperial (e.g. °F)

                <DataType>: DW - Day Of Week
                            WF - Weather Font Output
                            LT - Low Temp (current when today's conditions)
                            HT - High Temp (current when today's conditions)
                            CC - Current Conditions
                            CT - Conditions Text
                            PC - Precipitation Chance
                            HM - Humidity
                            WD - Wind Direction
                            WS - Wind Speed
                            WG - Wind Gusts
                            CN - City Name

                      Note: Only one data type should be given at any time

              <Day Number>: A number from 0 to 7 (0 = today, 7 = 7 days ahead)

```

Example conky config lines for today and tomorrow  based on above usage:

```
City Name: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M CN 0}

Day: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M DW 0}
Conditions: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M CC 0}
${font Weather:size=36}${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M WF 0}${font}
Temp: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M HT 0}
Wind: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M WS 0}
Humidity: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M HM 0}

Day: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M DW 1}
Conditions: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M CC 1}
${font Weather:size=36}${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M WF 1}${font}
High Temp: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M HT 1}
Low Temp: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M LT 1}
Wind: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M WS 1}
Humidity: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M HM 1}
Precipitation: ${execi 3600 python ~/scripts/conkyForecast.py UKXX0103 M PC 1}
```


If anyone can get together a conky config which uses the above to display several days forecasting nicely, and post it here, that would be great.

Any issues post back and I'll try to answer/fix ASAP. ANy suggestions for improvement are always welcome :)

Cheers

I see all this, but it there any way to get the forecast for tonight.  I like having today, tonight, and the future days.  Doing this allows me to see the change in weather in today which is nice

---

### Post by kaivalagi on 2008-04-15
> **yousillygoose said:**
> I would love to have this ability.  This is pretty much exactly what I am looking for  :)

Okay, I think once were done getting this right for most I'll need to re-post the solution for newcomers :)

See attached script, it now handles day ranges :)

I extended the previous example conky config I posted to now use the day range function, it works on all data types output.

```
${color1}${font Weather:size=30}${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M WF 0}${font}     ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M CC 0} , Humidity:${execi 3600 python ~/Scripts/conky//conkyForecast.py UKXX0103 M HM 0}
  ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 0}

${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M DW 1 3}
${font Weather:size=32}${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M WF 1 3}${font}
  ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 1 3}
```

There are several SPACER constants in the script that will need tweaking to suit you're needs, these match up with each data type that can be output. They are these lines:

```
	SPACING_DW = u" "
	SPACING_WF = u" "
	SPACING_LT = u"          "
	SPACING_HT = u"          "
	SPACING_CC = u" "
	SPACING_CT = u" "
	SPACING_PC = u"          "
	SPACING_HM = u"          "
	SPACING_WD = u"          "
	SPACING_WS = u"          "
	SPACING_WG = u"          "
	SPACING_CN = u"   "
```

I could extent the arguments so that YET another would be how many spaces between a ranged output, effectively making the SPACING constants defunct.

e.g. this:
```
 ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 1 3}
```
would become this:
```
 ${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 1 3 6}
```
Where the last "6" indicates that 6 spaces are required between each days output in the range...

Let me know what you think about it all anyway.

---

### Post by kaivalagi on 2008-04-15
> **yousillygoose said:**
> I see all this, but it there any way to get the forecast for tonight.  I like having today, tonight, and the future days.  Doing this allows me to see the change in weather in today which is nice

The xml retrieved from the weather.com site is in 2 parts. 1) current conditions 2) forecast data

In my script, the current conditions is used for todays weather, and the forecast data is used for subsequent days. It is the forecast data that can provide day and night details. Night details are currently ignored.

So yes in theory night data could be extracted, I will ponder on this one in case there is a way I can accommodate everything in a nice way. Maybe each data type passed in could have a D or N on the front, so HT would be DHT for daytime high temp, and NHT for nighttime hi temp...there is the question of current conditions not being used though...this idea doesn't fit well with current conditions data at all.

I am a little concerned that this script is going to get too all encompassing and just too damn complicated...I need to ponder on it a bit longer I think. 

This reminds me of my day job :) Ever changing functional specifications from the business...**if you have any other ideas up your sleeves please let me know before on make any more modifications!!! This goes for anyone else out there too! Any ideas you would like to see implemented in this script on the table ASAP please**. Then I can try to figure out what the bigger picture will be and lay the foundations for everything early on.

---

### Post by Bruce M. on 2008-04-15
> **kaivalagi said:**
> You got an eee pc/itx?

No, see my sig, it's an old desktop. The Eee is an overpriced PDA!
Mind you if I had the spare cash.   :)

> **kaivalagi said:**
> Do you thing there needs to be the ability to have a range of days setting for output?

i.e.

as well as this for a single day:
${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 1}

we have this to get back the next 5 days worth of something:
${execi 3600 python ~/Scripts/conky/conkyForecast.py UKXX0103 M HT 1 5}

I could look out for the last day_number argument say, and if present bring back a range of data, if not there then just bring back the one piece, if that makes sense. I could do this for all the available data types.

Users will need to tweak spacer settings in the script then though, and not arrange output through the conky config anymore...

Thanks for all your constructive feedback! :)

Yup, the three day forecast (4, 5 etc) works well.  I've tweaked the layout a bit too.  See attached.

And the code that did that:
```

background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
use_xft yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 0.5
update_interval 5.0
draw_shades no
draw_outline yes  # amplifies text if yes
draw_borders no
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
alignment bottom_left  # top_right, top_left, bottom_left, bottom_right
gap_x 10
gap_y 35
no_buffers yes  # Subtract file system buffers from used memory?
draw_outline yes
draw_shades yes  # shadecolor black
default_outline_color black
default_shade_color black

# Desde: ${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M CN 0}
# ${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M DW 0}
# Día: ${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M DW 1}

TEXT
${color cyan}${hr 1} $color
${color lightblue}Desde:${color} Buenos Aires, Argentina
${voffset 5}${color lightblue}Lat: ${color orange}34°35'S  ${color lightblue}Long: ${color orange}58°21'W ${alignr} ${color lightblue}Alt: ${color orange}25 m$color
${color lightblue}Ahora: ${color orange}Condiciones: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M CC 0}
${font Weather:size=50}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WF 0}${font}
${font Zekton:size=20}${offset 55}${voffset -48}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HT 0}${font}${color}
${color lightblue}${alignr 2}${voffset -30}Viento: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WS 0}
${alignr 2}${color lightblue}Humedad: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HM 0}
${color lightblue}Mañana: ${color orange}Condiciones: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M CC 1}
${offset 3}${font Weather:size=40}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WF 1}${font}
${color lightblue}${offset 35}${voffset -42}Max: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HT 1}${offset 67}${color lightblue}Min: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M LT 1}
${color lightblue}${offset 35}${voffset -3}Viento: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WS 1}${alignr 2}${color lightblue}Humedad: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HM 1}
${alignc}${color lightblue}Precipitaciones: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M PC 1}${color}
${color lightblue}Mañana2: ${color orange}Condiciones: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M CC 2}
${offset 3}${font Weather:size=40}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WF 2}${font}
${color lightblue}${offset 35}${voffset -42}Max: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HT 2}${offset 67}${color lightblue}Min: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M LT 2}
${color lightblue}${offset 35}${voffset -3}Viento: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WS 2}${alignr 2}${color lightblue}Humedad: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HM 2}
${alignc}${color lightblue}Precipitaciones: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M PC 2}${color}

```


But I see you have another toy for me to play with multiple days with less execi calls. Gotta give that one a run for the money. :lolflag:

Bruce

---

### Post by Bruce M. on 2008-04-15
> **kaivalagi said:**
> This reminds me of my day job :) Ever changing functional specifications from the business...**if you have any other ideas up your sleeves please let me know before on make any more modifications!!! This goes for anyone else out there too! Any ideas you would like to see implemented in this script on the table ASAP please**. Then I can try to figure out what the bigger picture will be and lay the foundations for everything early on.

Sounds fair enough, tell people no more development until you have a good solid "wish" list to work with.

And then make a promise not to promise any results.

If I could program I'd be right there in the thick of things.  :)

Here's an idea...

Your second script is GREAT! Very basic formatting that left the layout to each individual.  I hope you continue this method of either a very basic layout or better yet list each command on a separate line.

When I play with the latest where "we" can play with spaces I'll have to change my fonts to a "**mono**" font since a **"W"** is wider than an **"I"** if you get my drift. Variable width fonts play havoc with formatting unknown entries that a script will add.

Bruce
PS: Haven't forgot your translations to Spanish, haven't started yet except what I have seen.  :)

Clear = Despejado
Smoke = Humo (had a BIG fire in town today so it's smoke.)  :)

---

### Post by yousillygoose on 2008-04-15
Haha, I know i make a lot of suggestions, but two more:

Wind chill for winter
Feels like for summer

they would factor in what the weather actually feels like with humidity + wind.  Any thoughts?

---

### Post by kaivalagi on 2008-04-15
> **Bruce M. said:**
> Your second script is GREAT! Very basic formatting that left the layout to each individual. I hope you continue this method of either a very basic layout or better yet list each command on a separate line.

My latest script can do what the second one did as well as provide for ranges of data, best of both worlds approach. If you use your existing conky config with my latest script it should behave as before.

> **Bruce M. said:**
> When I play with the latest where "we" can play with spaces I'll have to change my fonts to a "mono" font since a "W" is wider than an "I" if you get my drift. Variable width fonts play havoc with formatting unknown entries that a script will add.

That variable width font issue you mentioned is definitely impossible to fix for conky. I have raised the question before now in the conky irc channel (#conky on irc.freenode.net) of whether html formatting could be put into conky, then we could use table formatting for layout, and everything would line up nicely. I have another side project using python and gtk+ to write transparently to the desktop as conky does but using html to do it....that's way off though, a  back burner :) Once I figure the basics I'd then have to start on retrieving all the system info...lots and lots of work...

> **Bruce M. said:**
> 
PS: Haven't forgot your translations to Spanish, haven't started yet except what I have seen.  :)

Clear = Despejado
Smoke = Humo (had a BIG fire in town today so it's smoke.)  :)

I've attached  the part of the script which drives the CC data type. It is basically a list of text versus condition codes. If you can provide an alternative list of condition text against the same id's I can do something with it. The general idea for language support (not sure whether it will work yet) is that I'll create a py file for each language, each containing the WeatherText class for that language, which will be loaded based on system locale from the main file. As people want other languages a translation of that py file can be made by them and added to the collection.

---

### Post by yousillygoose on 2008-04-15
looking over [http://xoap.weather.com/weather/local/08628?dayf=5&prod=xoap&par=1048871467&key=12daac2f3a67cb39](http://xoap.weather.com/weather/local/08628?dayf=5&prod=xoap&par=1048871467&key=12daac2f3a67cb39) which just happens to be the one for my area i slowly can understand your code  :).  So for my previous questions a section would need to be added to the script that took in 'n' for the present day, correct?


also, here is part of my script:

${execi 3600 python ~/scripts/conkyForecast.py 08628 I HT 0} / ${execi 3600 python ~/scripts/conkyForecast.py 08628 I LT 0}


This doesnt actually grab the high/low of todays weather.  It is just giving me current condition / current condition.

I know I'm asking a lot of questions but once I fully understand it all I probably can help more clueless people like myself!

---

### Post by kaivalagi on 2008-04-15
> **yousillygoose said:**
> Haha, I know i make a lot of suggestions, but two more:

Wind chill for winter
Feels like for summer

they would factor in what the weather actually feels like with humidity + wind.  Any thoughts?

You know of any formulae for calculating the feels like temperature based on wind speed and direction or humidity?

My first thoughts:

if condition = cloudy etc..
   temp = temp - (wind speed / 4)

if condition = sunny etc..
   temp = temp * (1+ ((humidity/100)/20)

 :lolflag:

Unfortunately there is no 'feels like' temperature data in the xml from weather.com...

P.S. Have you tried the new script with day ranges yet?

---

### Post by kaivalagi on 2008-04-15
> **yousillygoose said:**
> looking over [http://xoap.weather.com/weather/local/08628?dayf=5&prod=xoap&par=1048871467&key=12daac2f3a67cb39](http://xoap.weather.com/weather/local/08628?dayf=5&prod=xoap&par=1048871467&key=12daac2f3a67cb39) which just happens to be the one for my area i slowly can understand your code  :).  So for my previous questions a section would need to be added to the script that took in 'n' for the present day, correct?


also, here is part of my script:

${execi 3600 python ~/scripts/conkyForecast.py 08628 I HT 0} / ${execi 3600 python ~/scripts/conkyForecast.py 08628 I LT 0}


This doesnt actually grab the high/low of todays weather.  It is just giving me current condition / current condition.

I know I'm asking a lot of questions but once I fully understand it all I probably can help more clueless people like myself!

Yes, for today I override the forecast data with the current conditions, as it's more accurate. I've been thinking more on this...what about if no day_number is passed then we use current conditions, otherwise we use forecast data?

i.e.
${execi 3600 python ~/scripts/conkyForecast.py 08628 I LT} or ${execi 3600 python ~/scripts/conkyForecast.py 08628 I LT} would give todays current temp

${execi 3600 python ~/scripts/conkyForecast.py 08628 I HT 0} would give today's forecasted high
${execi 3600 python ~/scripts/conkyForecast.py 08628 I LT 0} would give today's forecasted low

[COLOR="Red"]Edit: done this already, script now returns current conditions when no day_number is provided. I'll hold back on posting and wait for a few more requirements. If you want a copy I'll PM it[/COLOR]

---

### Post by Bruce M. on 2008-04-15
> **yousillygoose said:**
> Haha, I know i make a lot of suggestions, but two more:

Wind chill for winter
Feels like for summer

they would factor in what the weather actually feels like with humidity + wind.  Any thoughts?

Good one

As long as "Wind chill" & "Feel like" is not "hard" coded but typed text because I'm used to Wind Chill and Humidity Index and in Spanish it all one: Sensacion Terimica (sp) or ST for short.

Either way they are exactly the same thing if you check it out. Just that TV channels and or web sites change the names to suit the season. Most I think in the US have adopted the "Feels Like" for year round use.

How about (for today)

Moon Rise - Salida (de la Luna) - 04:03pm or 16:03
Moon Set - Puesta (de la Luna) - 02:34am or 02:34
Phase (or Icon) - Waxing Gibbous, 81% Illuminated - need the Spanish for this  :)

and 
Sunrise - Amancer - 07:17am or 07:17
Sunset. - Atardecer - 06:29pm or 18:29

Just a thought.
Bruce

---

### Post by kenshin_i on 2008-04-15
I am using your script on the laptop, so, sometimes I am not connected to the internet.  When that happened, there will be a massive jumble across the screen.  Is there a way to return "Data Unavailable" or some sort?

---

### Post by kaivalagi on 2008-04-15
> **kenshin_i said:**
> I am using your script on the laptop, so, sometimes I am not connected to the internet.  When that happened, there will be a massive jumble across the screen.  Is there a way to return "Data Unavailable" or some sort?

I'll see what I can do, I will put in a check for internet connectivity to the weather.com server and if not found output a simple message of "No Connection Available"

The problem will be that if you are using the script multiple times in conky it will display the message multiple times...

---

### Post by yousillygoose on 2008-04-15
I will give the new script a whirl to see when i don't enter data what happens.  I will also check around for a feels like calculator and see if i can implement something helpful  :)

---

### Post by yousillygoose on 2008-04-15
can i get a copy of the updated one so i can try for current highs and lows.  You can pm or whatever you'd like.  ty

---

### Post by kaivalagi on 2008-04-16
Find script attached, just to re-cap:

Current conditions temp:
${execi 3600 python ~/scripts/conkyForecast.py 08628 I LT} 

Todays forecasted low temp:
${execi 3600 python ~/scripts/conkyForecast.py 08628 I LT 0} 

Tomorrows onwards low temp:
${execi 3600 python ~/scripts/conkyForecast.py 08628 I LT 1 7} 

Do you think having a further argument for the number of spaces wuld be useful, it would mean no messing with the spacer settings inside the script for ranges of output...e.g.

${execi 3600 python ~/scripts/conkyForecast.py 08628 I LT 1 7 7}

P.S I have reached the limit for upload for text files for this thread, now having to put into a tar.gz....

Have fun

---

### Post by yousillygoose on 2008-04-16
Okay, so for the new script how would i pull the data for tonights forcasted condition.  If i have this i can say current and tonights conditions to see if it is going to rain later  :)

---

### Post by kaivalagi on 2008-04-16
I have not put in day and night forecasts yet...I am still toying with the idea.

What I've done is enable current conditions and forecast data for today. e.g. day 0

The night forecast data, if pursued, will take a little time, I have to interrogate the xml and change the forecast data structure to cope before it will work. I am contemplating even handling the day/night forecast split until there is more of a requirement for it. I have never come across anyone else wanting this in other thread posts...and if tackled it will change the way the whole script works....

Do you know of others that want this feature?

---

### Post by yousillygoose on 2008-04-16
the last script i used had the feature of tonight which i loved (the script you commented about in the begining).  I use it only for tonight, no other nights.  It is nice because it is basically forecasted conditions for the rest of today, which is nice to have

---

### Post by mojohn on 2008-04-16
I installed Kaivalagi's py script, updated my .conkyrc file, and installed the weather fonts, all per his  instruction. However, when I run Conky, I get a repeating error message in the terminal that conky can't load font Weather:size=36.

Any ideas?

Thanks,

Mojohn

---

### Post by kaivalagi on 2008-04-17
Mojohn, could you post your conky config too please

---

### Post by wnelson on 2008-04-17
I modified different example of .conkyrc files to get to this point.

[ATTACH]66211[/ATTACH]

[ATTACH]66212[/ATTACH]

---

### Post by mojohn on 2008-04-17
I'll post my config file when I get home tonight.

mojohn

---

### Post by Cammy on 2008-04-17
So far so good.  I'm well on my way to getting this looking like my old one.

Is there any way to (or any plans to) have it display temps in high/low format?

Like: 80/72.

---

### Post by yousillygoose on 2008-04-17
you can do something like this  :

H/L: ${execi 3600 python ~/scripts/conkyForecast.py 08628 I HT 1} / ${execi 3600 python ~/scripts/conkyForecast.py 08628 I LT 1}

which posts something like 70 F / 55 F.

Is that what you're looking for?

---

### Post by Cammy on 2008-04-17
> **yousillygoose said:**
> you can do something like this  :

H/L: ${execi 3600 python ~/scripts/conkyForecast.py 08628 I HT 1} / ${execi 3600 python ~/scripts/conkyForecast.py 08628 I LT 1}

which posts something like 70 F / 55 F.

Is that what you're looking for?

Yep!  But I don't think I want 2 execis per day for that, so I'll think of another way to have the display.  I'm currently wrestling with the current conditions (I seem to be able to get either "clear" or "sunny" but no other info).

---

### Post by yousillygoose on 2008-04-17
hmm.  I don't think of a way to do it without two exec calls.  You would need the high and low data for the information.  Either way the script would do it automatically or you would have to do it with exec's.  I guess it could be programmed in to just be part of the script but it may be pointless

---

### Post by Cammy on 2008-04-17
Yeah it's cool.  I was just trying to recreate my old weather conky, which gave temps in high/low format by default.  If you did one execi and told it three days, you'd get hi/low hi/low hi/low.

I'm reformatting mine now based on the info available from this new weather script.  Right now I'm having a problem with the spaces.  This should give me two spaces, right?

${execi 3600 python ~/.scripts/conkyForecast.py USXX1234 I WF 0 4 2}

The '0' starts today, the '4' gives me 4 days after it, and the '2' is the spaces between, no?

---

### Post by kaivalagi on 2008-04-17
> **Cammy said:**
> Yeah it's cool.  I was just trying to recreate my old weather conky, which gave temps in high/low format by default.  If you did one execi and told it three days, you'd get hi/low hi/low hi/low.

I'm reformatting mine now based on the info available from this new weather script.  Right now I'm having a problem with the spaces.  This should give me two spaces, right?

${execi 3600 python ~/.scripts/conkyForecast.py USXX1234 I WF 0 4 2}

The '0' starts today, the '4' gives me 4 days after it, and the '2' is the spaces between, no?

The number of spaces function isn't fully implemented yet, the last posted script was done to satisfy yousillygoose's requirement of current conditions and day forecast both being available for 'today'

I will crack on with more functionality at the weekend, I am having a hard time with development in my day job at present, so don't really feel like even looking at the script until I've had a timeout from it all.

Basically this:

```
output = output + self.SPACING_LT + string
#output = output + self.getSpaces(number_of_spaces) + string
```

needs to become etc etc:

```
#output = output + self.SPACING_LT + string
output = output + self.getSpaces(number_of_spaces) + string
```

and be thoroughly tested....feel free to have a play, if it doesn't work for you then wait for the weekend when I get it done (along with day/night options)

Cheers

---

### Post by kaivalagi on 2008-04-17
> **yousillygoose said:**
> the last script i used had the feature of tonight which i loved (the script you commented about in the begining).  I use it only for tonight, no other nights.  It is nice because it is basically forecasted conditions for the rest of today, which is nice to have

Expect a updated script at the weekend to provide day and night details for forecasted data.

I am a bit pissed at the moment, the last 2 months of development me and my team have been pushing hard to complete, needs a serious rewrite now, the business have just changed their requirements again #-o Keeps us all in jobs I guess :) gotta be a bright side to it...


The script will still have yet another parameter for day ('D') and night ('N')

So instead of this for a day forecast for the next 7 days:

```
${execi 3600 python ~/scripts/conkyForecast.py 08628 I LT 1 7} 
```

It would be:

```
${execi 3600 python ~/scripts/conkyForecast.py 08628 I LT D 1 7} 
```

and then this for nighttime equivalent:

```
${execi 3600 python ~/scripts/conkyForecast.py 08628 I LT N 1 7} 
```

A 'D' or 'N' would always be required when using the forecast data, they wouldn't be needed (or do anything) for current conditions.

I don't want to combine the day / night data in one execi call as this will then not suit everyone else that doesn't want night data for example. Does this sound like something that will suit?

Edit: I think I will have to start looking at command argument parsing soon, so any combination of options can be given and there are defaults when nothing is provided...so rather than LT it would be --datatype:LT for example

---

### Post by moore.bryan on 2008-04-17
any hope for those of us behind a proxy?  not working here...
EDIT
just kidding... it suddenly and magically decided to start working...

---

### Post by mojohn on 2008-04-17
Kaivalagi, my conkyrc and conkyforecast.py files.

Thanks, mojohn

---

### Post by kaivalagi on 2008-04-18
> **moore.bryan said:**
> any hope for those of us behind a proxy?  not working here...
EDIT
just kidding... it suddenly and magically decided to start working...

Worth considering adding proxy settings to the script do you think? Have them switched off by default...

---

### Post by kaivalagi on 2008-04-18
> **mojohn said:**
> Kaivalagi, my conkyrc and conkyforecast.py files.

Your script didn't work for me either until I changed the use_xft setting."**use_xft no**" needs to be "**use_xft yes**".

Use Xft is for anti-aliased font support, hence the requirement for the weather font.

Cheers,
Mark

---

### Post by kaivalagi on 2008-04-18
I'm implementing the day / night forecasting now and there is a fundamental flaw, the temperatures are not day / night specific. I assume a LT is night temp and a HT is day temp....

The conditions text etc is day or night specific. Once I'm done you'll have to have a play with it and see what you make of it...

Cheers

---

### Post by mojohn on 2008-04-18
Kaivalagi, I now see the weather fonts, but the font size of the text is now large enough that I can't see the entire conky display on my screen (see attached). How do I shrink the font size for the text?

FWIW, I like having bigger text than the default, but not quite this big.

Thanks,

mojohn

---

### Post by kaivalagi on 2008-04-18
conkyForecast.tar.gz is attached with a new script and an example conky file.

Since the first script the following modifications have been done:

- Allow day ranges for forecast data
- Check for connectivity to xoap service
- Allow the setting of spaces for ranged output
- Allow Night and Day forecast output
- Support locale for condition code text "CC" option, awaiting Spanish language translation
- Use pickling to load and save cached class data, this bypasses the need to interrogate cached data when no web service call is required
[COLOR="Blue"]Edits:
- Added spanish condition text - work in progress - Thanks Bruce M
- Added isnumeric check on all numeric output with units suffix, only suffixed when numeric
- Altered pickle file naming to include location code, new data is fetched right away if location is changed
- Added spanish week days conversion via locale
- Bearing wind direction always returned in the form NNE etc, bearings are converted
[/COLOR]
The example conky file will need amendments to point to your conkyForecast script location. Also note that due to the amounts of execi calls in the test conky file (to test nearly all data types for current and a 7 day forecast) it takes a while for conky to start. I suggest using the test conky file as a template only. You really don't need all the data it displays! :)

Any issues give me a shout, I'll be about this weekend to answer questions.

Enjoy :-D

Usage now as follows:

```
conkyForecast.py <Loc Code> <Units> <Data Type> [<Day Night Flag> [<Start Day #> [<End Day #>  <Spaces #> ]]]

     Where <Loc Code>: Use the following url to determine your 
                       location code by city name:
                       http://xoap.weather.com/search/search?where=Norwich

               <Unit>: M = Metric (e.g. °C)
                       I = Imperial (e.g. °F)

          <Data Type>: DW - Day Of Week
                       WF - Weather Font Output
                       LT - Low Temp (Low=High when current conditions)
                       HT - High Temp (Low=High when current conditions)
                       CC - Current Conditions (Locale specific once translations provided!)
                       CT - Conditions Text
                       PC - Precipitation Chance
                       HM - Humidity
                       WD - Wind Direction
                       WS - Wind Speed
                       WG - Wind Gusts
                       CN - City Name

     <Day Night Flag>: Optional. If not passed current conditions are provided.
                       D - Day forecast
                       N - Night forecast

        <Start Day #>: Optional. Can only be used if day night flag is given.
                       Today = 0, Tomorrow = 1, Maximum = 7

          <End Day #>: Optional. Can only be used if start day # is given. 
                       Today = 0, Tomorrow = 1, Maximum = 7

           <Spaces #>: Optional. Must be used if end day # is given.
                       The number of spaces to use between each day #'s data.

    Note: Only one data type should be given at any time
          If both day #'s are provided a range of forecast data is output.
          If only a start day # is given, that day #'s forecast is output.
          If day night flag and both day #'s are omitted current conditions are output.
```

---

### Post by kaivalagi on 2008-04-18
> **mojohn said:**
> Kaivalagi, I now see the weather fonts, but the font size of the text is now large enough that I can't see the entire conky display on my screen (see attached). How do I shrink the font size for the text?

FWIW, I like having bigger text than the default, but not quite this big.

Thanks,

mojohn

You need to set the default font etc like this:

```
xftfont Terminus:size=9
```

You can set the font to whatever you'd like, and change the size (and even make it bold if you want)

Take a look at the test conky file in the  latest attachment I posted. Alternatively there is a good help doc on the conky site here: [http://conky.sourceforge.net/documentation.html]("http://conky.sourceforge.net/documentation.html")

I highly recommend having a look at some of the example conky files on the conky site and/or the ones posted in this thread: [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865") You'll get lots of ideas on what you can and can't do with conky then.

Hope that helps :)

---

### Post by dccrens on 2008-04-18
Anyone have a problem with the weather font displaying multiple icons for a day? This causes my conky to be very wide if I use more than one day in the forecast. See attached gz screenshot. 

I am using

```
${color7}WEATHER${hr 2}$color
${color2}Station Name: $color${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I CN}
${color2}Conditions: $color${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I CT} & ${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I CC}${font Weather:size=24}${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I WF}${font :size=8} ${color2}Temp: $color${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I HT}/${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I LT}

${color2}${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 M DW} ${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 M DW D 1 2} 
${font Weather:size=24}${color2}${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 M CC}${color2}${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 M CC D 0 2}${font :size=8}
```

Seems like if the day conditions predict "Partly Cloudy Thunderstorms" as output of:
```
 python ~/Scripts/conkyForecast.py USVA0427 M CC D 0 2 
```

Then when run with the
```
 ${font Weather:size=24}
```
 I get three wide icons depicting it. 

I have tried reinstallling the weather font. Seems to install fine.

---

### Post by dccrens on 2008-04-18
Nevermind... So stupid of me... I wasn't using the WF option...

---

### Post by Bruce M. on 2008-04-18
Hi Folks ...

Wow!!  Conky Weather Python Script Based On Metar v.1 is really growing up in a hurry here.

I've been busy with other things lately and haven't had much time to keep up, I'm still using one of the earlier scripts. It suits my needs for the moment and I thought I'd share it with you for one simple reason ... it is almost totally in Spanish. Heavily flavoured for Argentina obviously.

my **conkymain** file:
```

background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
use_xft	yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 0.5
update_interval 5.0
draw_shades no
draw_outline yes  # amplifies text if yes
draw_borders no
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
alignment top_right  # or top_left, bottom_left, bottom_right
gap_x 10
gap_y 35
no_buffers yes  # Subtract file system buffers from used memory?
draw_outline yes
draw_shades yes  # shadecolor black
default_outline_color black
default_shade_color black

# ${voffset -30}${alignc 90}${font openlogos:size=100}${color lightblue}v$color$font
# ${voffset -40}${font Zekton:size=11}${color lightblue}${alignc}*** ${color orange}GMT ${color white}${tztime GMT %H:%M} ${color lightblue}***$color$font

TEXT
${font Zekton:size=11}${color lightblue}${alignc}*** ${color orange}GMT ${color white}${tztime GMT %H:%M} ${color lightblue}***$color$font
${font Zekton:size=11}${alignc}${Color orange}** ${color lightblue}Canada ${color orange}**$color$font
${color lightblue}Winnipeg${color lightblue}: ${color white}${tztime Canada/Central %H:%M}$color${alignr 2}${color lightblue}London${color lightblue}: ${color white}${tztime Canada/Eastern %H:%M}$color
${color cyan}${hr 1}$color
${alignc}${color lightblue}--> ${alignc}${color white}${exec whoami} @ $nodename ${color lightblue}<--$color
${alignc}${color orange}$sysname $kernel ($machine)$color
${font Zekton:size=20}${color white}${alignc}${time %H:%M}$color$font
${font Zekton:size=12}${color lightblue}${alignc}${time %A, %d %b. %Y}$color$font
${color yellow}UpTime:${alignr}$uptime$color
${color cyan}${hr 1}$color
${voffset 5}${color orange}System Temps:${color lightblue}${alignr 2}( Low = 0°C / High = 127°C )$color
${voffset 5}${color yellow}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c1-19| sed '/^$/d'}$color
${color cyan}${hr 1}$color
${voffset 5}${color orange}CPU:${color} ${cpu} % ${color orange}${cpubar cpu0}$color
${color lightblue}Freq: ${color white}$freq ${color lightblue}MHz${alignr 2}${color lightblue}Processes: ${color}$running_processes ${color lightblue}/ ${color}$processes
${color lightblue}Load Avg (${color yellow}Min${color lightblue}):$alignr${color yellow}1: ${color white}${loadavg 1}   ${color yellow}5: ${color white}${loadavg 2}   ${color yellow}15: ${color white}${loadavg 3} ${color orange}$color
${voffset 5}${color orange}MEM: ${color lightblue}RAM: ${color white}$memperc% ${color lightblue}(${color white}${mem} ${color lightblue}of ${color orange}${memmax}${color lightblue}) ${color orange}$membar $color
${color lightblue}Buffered: ${color white}${buffers}$color${alignr 2}${color lightblue}Cached:${color white} ${cached}$color
${voffset 5}${color orange}SWAP: ${color white}$swapperc% ${color lightblue}(${color white}$swap ${color lightblue}of ${color orange}${swapmax}${color lightblue})${color orange} ${swapbar}$color
${voffset 5}${color orange}HD Info${color lightblue} - ${color white}Free${color lightblue} - Used - ${color orange} Total ${color cyan}${hr 1}$color
${voffset 5}${color lightblue}sda1 /:${offset 6}${color white}${fs_free_perc /} % = ${fs_free}${alignr 2}${color lightblue}${fs_used /}${color white} of ${color orange}${fs_size /}$color
${color lightblue}/home: ${color white}${fs_free_perc /home/bruloo} % = ${fs_free}  ${alignr 2}${color lightblue}${fs_used /home/bruloo}${color white} of ${color orange}${fs_size /home/bruloo}$color
${color lightblue}sdb1:${offset 14}${color white}${fs_free_perc /media/sdb1} % = ${fs_free /media/sdb1}${alignr 2}${color lightblue}${fs_used /media/sdb1}${color white} of ${color orange}${fs_size /media/sdb1}$color
${color lightblue}W2K:${offset 11}${color white}${fs_free_perc /media/sda1} % = ${fs_free /media/sda1}${alignr 2}${color lightblue}${fs_used /media/sda1}${color white} of ${color orange}${fs_size /media/sda1}$color
${color cyan}${hr 1} $color
${color lightblue}Desde:${color} Buenos Aires, Argentina
${color lightblue}Lat: ${color orange}34°35'S  ${color lightblue}Long: ${color orange}58°21'W ${alignr} ${color lightblue}Alt: ${color orange}25 m$color
${voffset 5}${color lightblue}Hoy: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M CC 0}
${font Weather:size=50}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WF 0}${font}
${alignc 40}${font Zekton:size=20}${voffset -48}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HT 0}${font}${color}
${color lightblue}${alignr 2}${voffset -30}Viento: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WS 0}
${alignr 2}${color lightblue}Humedad: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HM 0}
${voffset 5}${color lightblue}Mañana: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M CC 1}
${offset 3}${font Weather:size=40}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WF 1}${font}
${alignc 10}${color lightblue}${voffset -42}Max: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HT 1}${alignr 37}${color lightblue}Min: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M LT 1}
${alignc -14}${color lightblue}${voffset -3}Viento: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WS 1}${alignr 2}${color lightblue}Humedad: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HM 1}
${alignc 8}${color lightblue}Precipitaciones: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M PC 1}${color}
${voffset 5}${color lightblue}Mañana pasado: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M CC 2}
${offset 3}${font Weather:size=40}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WF 2}${font}
${alignc 10}${color lightblue}${voffset -42}Max: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HT 2}${alignr 37}${color lightblue}Min: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M LT 2}
${alignc -14}${color lightblue}${voffset -3}Viento: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M WS 2}${alignr 2}${color lightblue}Humedad: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HM 2}
${alignc 8}${color lightblue}Precipitaciones: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M PC 2}${color}
${color cyan}${hr 1}${color}
${voffset 5}${color orange}IP:${alignc}${color white}${addr eth0}$color
${color lightblue}Down: ${color white}${downspeed eth0}k/s ${alignr}${color lightblue}Up: ${color white}${upspeed eth0}k/s $color
${color lightblue}Total: ${color white}${totaldown eth0} ${alignr}${color lightblue}Total: ${color white}${totalup eth0} $color
${color lightblue}Inbound: ${color white}${tcp_portmon 1 32767 count}          ${color lightblue}Outbound: ${color white}${tcp_portmon 32768 61000 count}${alignr}${color lightblue}Total: ${color white}${tcp_portmon 1 65535 count} $color
${voffset 5}${color orange}Connections: ${color white}${tcp_portmon 32768 61000 count} ${alignr} ${color orange}Service/Port $color
${voffset 5}${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}$color

```

and my **conkyForecast.py**

```

#!/usr/bin/python
# -*- coding: iso-8859-15 -*-
###############################################################################
# conkyForecast.py is a simple python script to gather details of the 
# current weather for use in conky, where textual content is only valid.
#
#  Author: Kaivalagi
# Created: 13/04/2008

import sys, os, urllib2, datetime, time
from xml.dom import minidom
from stat import *
import locale
import gettext

APP="conkyForecast.py"
DIR=os.path.dirname (__file__) + '/locale'
gettext.bindtextdomain(APP, DIR)
gettext.textdomain(APP)
_ = gettext.gettext

DEGREE = "°"
USAGE_TEXT = """
 conkyForecast.py is a simple python script to gather details of the 
 current weather for use in conky, where textual content is only valid.

 Usage: conkyForecast.py <Location Code> <Units> <Data Type> <Day Number>

     Where <Location Code>: Use the following url to determine your 
                            location code by city name:
                            http://xoap.weather.com/search/search?where=Norwich

                    <Unit>: M = Metric (e.g. °C)
                            I = Imperial (e.g. °F)

                <DataType>: DW - Day Of Week
                            WF - Weather Font Output
                            LT - Low Temp (current when today's conditions)
                            HT - High Temp (current when today's conditions)
                            CC - Current Conditions
                            CT - Conditions Text
                            PC - Precipitation Chance
                            HM - Humidity
                            WD - Wind Direction
                            WS - Wind Speed
                            WG - Wind Gusts
                            CN - City Name

                      Note: Only one data type should be given at any time
"""

class Forecast:
	def __init__(self, day_of_week, low, high, condition_code, condition_text, precip, humidity, wind_dir, wind_speed, wind_gusts, city):
		self.day_of_week = day_of_week
		self.low = low
		self.high = high
		self.condition_code = condition_code
		self.condition_text = condition_text
		self.precip = precip
		self.humidity = humidity
		self.wind_dir = wind_dir
		self.wind_speed = wind_speed
		self.wind_gusts = wind_gusts
		self.city = city

class WeatherText:

	conditions_text = {
		"0": _("Tornado"),
		"1": _("Tormenta Tropical"),
		"2": _("Huracán"),
		"3": _("Tormentas Severas"),
		"4": _("Tormentas"),
		"5": _("Mixed Rain and Snow"),
		"6": _("Mixed Rain and Sleet"),
		"7": _("Mixed Precipitation"),
		"8": _("Freezing Drizzle"),
		"9": _("Llovizna"),
		"10": _("Freezing Rain"),
		"11": _("Chaparrones"),
		"12": _("Chaparrones"),
		"13": _("Snow Flurries"),
		"14": _("Light Snow Showers"),
		"15": _("Blowing Snow"),
		"16": _("Nieve"),
		"17": _("Granizo"),
		"18": _("Aguanieve"),
		"19": _("Polvo"),
		"20": _("Niebla"),
		"21": _("Haze"),
		"22": _("Humo"),
		"23": _("Blustery"), 
		"24": _("Windy"),
		"25": _("Frío"),
		"26": _("Nublado"),
		"27": _("Mayormente Nublado"),
		"28": _("Mayormente Nublado"),
		"29": _("Parcialmente Nublado"),
		"30": _("Parcialmente Nublado"),
		"31": _("Despejado"),
		"32": _("Despejado"),
		"33": _("Algo Nublado"),
		"34": _("Algo Nublado"),
		"35": _("Mixed Rain and Hail"),
		"36": _("Calor"),
		"37": _("Tormentas Aisladas"),
		"38": _("Tormentas Dispersadas"),
		"39": _("Tormentas Dispersadas"),
		"40": _("Chubascos Dispersos"),
		"41": _("Heavy Snow"),
		"42": _("Scattered Snow Showers"),
		"43": _("Nieve Pesada"),
		"44": _("Nubes Dispersas"),
		"45": _("Thunder Showers"),
		"46": _("Snow Showers"),
		"47": _("Tormentas Aisladas"),
		"na": _("N/A"),
		"-": _("N/A")
	}

	conditions_weather_font = {
		"0": _("W"),
		"1": _("V"),
		"2": _("W"),
		"3": _("s"),
		"4": _("p"),
		"5": _("k"),
		"6": _("k"),
		"7": _("g"),
		"8": _("g"),
		"9": _("g"),
		"10": _("h"),
		"11": _("g"),
		"12": _("g"),
		"13": _("k"),
		"14": _("k"),
		"15": _("k"),
		"16": _("k"),
		"17": _("k"),
		"18": _("k"),
		"19": _("e"),
		"20": _("e"),
		"21": _("a"),
		"22": _("d"),
		"23": _("d"), 
		"24": _("d"),
		"25": _("d"),
		"26": _("e"),
		"27": _("e"),
		"28": _("e"),
		"29": _("c"),
		"30": _("c"),
		"31": _("a"),
		"32": _("a"),
		"33": _("b"),
		"34": _("b"),
		"35": _("k"),
		"36": _("a"),
		"37": _("f"),
		"38": _("f"),
		"39": _("f"),
		"40": _("g"),
		"41": _("k"),
		"42": _("k"),
		"43": _("k"),
		"44": _("b"),
		"45": _("g"),
		"46": _("k"),
		"47": _("f"),
		"na": _("N/A"),
		"-": _("N/A")
	}
	
	day_of_week = {
		"Monday": _("Monday"),
		"Tuesday": _("Tuesday"),
		"Wednesday": _("Wednesday"),
		"Thursday": _("Thursday"),
		"Friday": _("Friday"),
		"Saturday": _("Saturday"),
		"Sunday": _("Sunday")
	}

  
class GlobalWeather:

	forecast = []
	locale_lang = "en"

	location_code = ""
	units = ""
	data_type = ""
	currentxmldoc = ""
	forecastxmldoc = ""

 	TEMP_FILEPATH_CURRENT_M = "/tmp/globalweather-current-m.xml"
	TEMP_FILEPATH_FORECAST_M = "/tmp/globalweather-forecast-m.xml"
 	TEMP_FILEPATH_CURRENT_I = "/tmp/globalweather-current-i.xml"
	TEMP_FILEPATH_FORECAST_I = "/tmp/globalweather-forecast-i.xml"
 	EXPIRY_MINUTES_CURRENT = 10
	EXPIRY_MINUTES_FORECAST = 90

	def __init__(self,location_code,units):

		try:
			self.location_code = location_code
			self.units = units
			self.locale_lang = locale.getdefaultlocale()[0][0:2]
		except:
			print "locale not set"

	def getText(self,nodelist):
		rc = ""
		for node in nodelist:
			if node.nodeType == node.TEXT_NODE:
				rc = rc + node.data
		return rc

        def fetch_data(self):

		# determine the file paths we will use
		if self.units == "M":
			file_path_current = self.TEMP_FILEPATH_CURRENT_M
			file_path_forecast = self.TEMP_FILEPATH_FORECAST_M
		else:
			file_path_current = self.TEMP_FILEPATH_CURRENT_I
			file_path_forecast = self.TEMP_FILEPATH_FORECAST_I

 		# does the data need retrieving again?
 		if os.path.exists(file_path_current):
 			lastmodDate = time.localtime(os.stat(file_path_current)[ST_MTIME])
			expiryDate = (datetime.datetime.today() - datetime.timedelta(minutes=self.EXPIRY_MINUTES_CURRENT)).timetuple()

			if expiryDate > lastmodDate:
				RefetchCurrentData = True
			else:
				RefetchCurrentData = False
		else:
			RefetchCurrentData = True

		#print "refetch current:",RefetchCurrentData

                # fetch the current conditions data, either from the website or by 'unpickling'
 		if RefetchCurrentData == True:

			# current conditions data
 			url = 'http://xoap.weather.com/weather/local/' + self.location_code + '?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39'
			if self.units == "M":
                        	url = url + '&unit=m'
			try:
				usock = urllib2.urlopen(url)
				xml = usock.read()
				usock.close()
				self.currentxmldoc = minidom.parseString(xml)
				fileoutput = open(file_path_current, 'w')
 				fileoutput.write(xml)
		 		fileoutput.close()
			except:
				print "Unexpected error: ", sys.exc_info()[0]
				print "Unable to contact weather source for current conditions"
		else:
 			fileinput = open(file_path_current, 'r')
			xml = fileinput.read()
			fileinput.close()
			self.currentxmldoc = minidom.parseString(xml)

 		# does the data need retrieving again?
 		if os.path.exists(file_path_forecast):
 			lastmodDate = time.localtime(os.stat(file_path_forecast)[ST_MTIME])
			expiryDate = (datetime.datetime.today() - datetime.timedelta(minutes=self.EXPIRY_MINUTES_FORECAST)).timetuple()

			if expiryDate > lastmodDate:
				RefetchForecastData = True
			else:
				RefetchForecastData = False
		else:
			RefetchForecastData = True

		#print "refetch forecast:",RefetchForecastData

                # fetch the forecast data, either from the website or by 'unpickling'
 		if RefetchForecastData == True:

			# current conditions data
 			url = 'http://xoap.weather.com/weather/local/' + self.location_code + '?dayf=5&prod=xoap&par=1048871467&key=12daac2f3a67cb39'
			if self.units == "M":
                        	url = url + '&unit=m'
			try:
				usock = urllib2.urlopen(url)
				xml = usock.read()
				usock.close()
				self.forecastxmldoc = minidom.parseString(xml)
				fileoutput = open(file_path_forecast, 'w')
 				fileoutput.write(xml)
		 		fileoutput.close()
			except:
				print "Unexpected error: ", sys.exc_info()[0]
				print "Unable to contact weather source for forecast"
		else:
 			fileinput = open(file_path_forecast, 'r')
			xml = fileinput.read()
			fileinput.close()
			self.forecastxmldoc = minidom.parseString(xml)	

	def prepare_data(self):

		try:
			self.forecast = []

			#current conditions
			day_of_week = "Hoy"
			weather_n = self.currentxmldoc.documentElement
			location_n = weather_n.getElementsByTagName('loc')[0]
			city_n = location_n.getElementsByTagName('dnam')[0]
			city = self.getText(city_n.childNodes)
			sunrise_n = location_n.getElementsByTagName('sunr')[0]
			sunrise = self.getText(sunrise_n.childNodes)
			sunset_n = location_n.getElementsByTagName('suns')[0]
			sunset = self.getText(sunset_n.childNodes)
			current_condition_n = weather_n.getElementsByTagName('cc')[0]
			current_desc_n = current_condition_n.getElementsByTagName('t')[0]
			current_desc = self.getText(current_desc_n.childNodes)
			current_code_n = current_condition_n.getElementsByTagName('icon')[0]
			current_code = self.getText(current_code_n.childNodes)
			current_temp_n = current_condition_n.getElementsByTagName('tmp')[0]
			current_temp = self.getText(current_temp_n.childNodes)
			current_temp_feels_n = current_condition_n.getElementsByTagName('flik')[0]
			current_temp_feels = self.getText(current_temp_feels_n.childNodes)
			bar_n = current_condition_n.getElementsByTagName('bar')[0]
			bar_read_n = bar_n.getElementsByTagName('r')[0]
			bar_read = self.getText(bar_read_n.childNodes)
			bar_desc_n = bar_n.getElementsByTagName('d')[0]
			bar_desc = self.getText(bar_desc_n.childNodes)
			wind_n = current_condition_n.getElementsByTagName('wind')[0]
			wind_speed_n = wind_n.getElementsByTagName('s')[0]
			wind_speed = self.getText(wind_speed_n.childNodes)
			wind_gust_n = wind_n.getElementsByTagName('gust')[0]
			wind_gusts = self.getText(wind_gust_n.childNodes)
			wind_dir_n = wind_n.getElementsByTagName('d')[0]
			wind_direction = self.getText(wind_dir_n.childNodes)
			humidity_n = current_condition_n.getElementsByTagName('hmid')[0]
			humidity = self.getText(humidity_n.childNodes)
			moon_n = current_condition_n.getElementsByTagName('moon')[0]
			moon_phase_n = moon_n.getElementsByTagName('t')[0]
			moon_phase = self.getText(moon_phase_n.childNodes)
			day_forecast = Forecast(day_of_week, current_temp, current_temp, current_code, current_desc, "N/A", humidity, wind_direction, wind_speed, wind_gusts, city)
			self.forecast.append(day_forecast)

			# forecast data
			weather_n = self.forecastxmldoc.documentElement
			location_n = weather_n.getElementsByTagName('loc')[0]
			city_n = location_n.getElementsByTagName('dnam')[0]
			city = self.getText(city_n.childNodes)
			forecast_n = weather_n.getElementsByTagName('dayf')[0]
			day_nodes = forecast_n.getElementsByTagName('day')
	
			for day in day_nodes:
				if day.getAttribute('d') != "0": # ignore today, covered by above
					day_of_week = day.getAttribute('t')
					day_of_year = day.getAttribute('dt')
					high_temp_n = day.getElementsByTagName('hi')[0]
					high_temp = self.getText(high_temp_n.childNodes)
					low_temp_n = day.getElementsByTagName('low')[0]
					low_temp = self.getText(low_temp_n.childNodes)
					daytime_n = day.getElementsByTagName('part')[0]
					condition_code_n = daytime_n.getElementsByTagName('icon')[0]
					condition_code = self.getText(condition_code_n.childNodes)
					condition_n = daytime_n.getElementsByTagName('t')[0]
					condition = self.getText(condition_n.childNodes)
					precip_n = daytime_n.getElementsByTagName('ppcp')[0]
					precip = self.getText(precip_n.childNodes)
					humidity_n = daytime_n.getElementsByTagName('hmid')[0]
					humidity = self.getText(humidity_n.childNodes)
					wind_n = daytime_n.getElementsByTagName('wind')[0]
					wind_speed_n = wind_n.getElementsByTagName('s')[0]
					wind_speed = self.getText(wind_speed_n.childNodes)
					wind_direction_n = wind_n.getElementsByTagName('t')[0]
					wind_direction = self.getText(wind_direction_n.childNodes)
					wind_gusts_n = wind_n.getElementsByTagName('gust')[0]
					wind_gusts = self.getText(wind_gusts_n.childNodes)
					day_forecast = Forecast(day_of_week, low_temp, high_temp, condition_code, condition, precip, humidity, wind_direction, wind_speed, wind_gusts, city)
					self.forecast.append(day_forecast) 	
		except:
			print "prepare_data:Unexpected error: ", sys.exc_info()[0]

	def output_data(self,data_type,day_number):
		try:
			# Weather.com's TOS state that I'm not supposed to change their text.  However, I asked them, and they do not
			# supply non-English weather descriptions.  So, if the current locale uses an English language, use weather.com's
			# description... otherwise, use our own.
			#if self.locale_lang == "en":
			#	self.titleText = self.city + ": " + self.current_desc + ", " + self.current_temp + u"\u00B0"
			#else:
			#	self.titleText = self.city + ": " + WeatherText.conditions_text[self.current_code] + ", " + self.current_temp + u"\u00B0"			

			# define current units for output
			if self.units == "M":
				tempunit = DEGREE+"C"
				speedunit = "kph"
			else:
				tempunit = DEGREE+"F"
				speedunit = "mph"

			# determine the required data type and output formatted text
			if data_type == "DW":
				print self.forecast[int(day_number)].day_of_week
			elif data_type == "WF": # weather font
				print WeatherText.conditions_weather_font[self.forecast[int(day_number)].condition_code]
			elif data_type == "LT":
				print self.forecast[int(day_number)].low,tempunit
			elif data_type == "HT":
				print self.forecast[int(day_number)].high,tempunit
			elif data_type == "CC":
				#print "%s"%self.forecast[int(day_number)].condition_code
				print WeatherText.conditions_text[self.forecast[int(day_number)].condition_code]
			elif data_type == "CT":
				print self.forecast[int(day_number)].condition_text
			elif data_type == "PC":
				print self.forecast[int(day_number)].precip,"%"
			elif data_type == "HM":
				print self.forecast[int(day_number)].humidity,"%"
			elif data_type == "WD":
				print self.forecast[int(day_number)].wind_dir
			elif data_type == "WS":
				print self.forecast[int(day_number)].wind_speed,speedunit
			elif data_type == "WG":
				print self.forecast[int(day_number)].wind_gusts,speedunit
			elif data_type == "CN":
				print self.forecast[int(day_number)].city
			else:
				print USAGE_TEXT
				print "ERROR:Unknown data type requested"
		except:
			print "output_data:Unexpected error: ", sys.exc_info()[0]

if __name__ == "__main__":

	if len(sys.argv) < 5:
		print USAGE_TEXT
		print "ERROR:Incorrect arguments given."
 	else:

		location_code = sys.argv[1] # same as yahoo weather codes
		units = sys.argv[2] #M/I
 		data_type = sys.argv[3]
		day_number = sys.argv[4] # 0 for current, 1-7 for future days up to a weeks time

		# create new global weather object
		weather = GlobalWeather(location_code, units)
		weather.fetch_data()
		weather.prepare_data()
		weather.output_data(data_type, day_number)


```
and last but not least a screenie ...

Have a nice day!
Bruce

---

### Post by dccrens on 2008-04-18
Finally finished! Thanks to all of you for a great thread and a great script. Here is my conkyrc and a screen shot.

```

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external Scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#
# Possible variables to be used:
# EDITED OUT....

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# Create own window instead of using desktop (required in nautilus)
own_window yes
#own_window_type root
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
# Use double buffering (reduces flicker, may not work for everyone)

#own_window_type override
#own_window_transparent yes
#own_window_hints undecorated,sticky,skip_taskbar,skip_pager
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

#Set average sampling
cpu_avg_samples 2
net_avg_samples 2

# fiddle with window
use_spacer yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

#Oulines and Shades
draw_outline yes
draw_shades yes
# shadecolor black
default_outline_color black
default_shade_color black

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.5

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
color0 red
color1 lightblue
color2 turquoise
color3 gold
color4 green
color5 white
color6 yellow
color7 orange
color8 blue
color9 lightgreen

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 50

# stuff after 'TEXT' will be formatted on screen

TEXT
${font :size=12}${color2}${alignc}${time %H:%M}$color$font
${font :size=8}${color5}${alignc}${time %A, %d %b. %Y}$color${font :size=8}
${color yellow}UpTime:${alignr}$uptime${color}
${color7}SYSTEM ${hr 2}${color}
${color2}${pre_exec echo $USERNAME} on $nodename $sysname
${color7}CPU ${hr 2}$color
  ${color4}FREQ:${color0}${freq}MHz$color ${color4}Core0 Temp: ${color0}${execi 8 sensors | grep -A 1 'Core 0' | cut -c15-16 | sed '/^$/d'}C ${color4}Core1 Temp: ${color0}${execi 8 sensors | grep -A 1 'Core 1' | grep -A 1 'high' | cut -c15-16 | sed '/^$/d'}C
  ${color4}CPU0 ${color3}${cpu cpu1}% ${color2}${cpubar 6 cpu1}${color}
  ${color4}CPU1 ${color3}${cpu cpu2}% ${color2}${cpubar 6 cpu2}${color}
  ${color4}CPU Load ${alignr}${color black}${cpugraph 10,230 000000 FF4900}
${color7}TEMPS ${hr 2}$color
  ${color4}CPU Temp: ${color5}${i2c 9191-0290 temp 2}C ${alignr}${color4}GPU Temp: ${color5}${execi 300 nvidia-settings -q GPUCoreTemp | grep "caver" | cut -d ':' -f3 | cut -d ' ' -f2 | cut -d '.' -f1 ;}C
  ${color4}CPU Fan Spd: ${color5}${i2c 9191-0290 fan 2} rpm ${alignr}${color4}${alignr}${color4}${exec nc localhost 7634 | cut -c2-9 ;}: ${color5}${execi 300 nc localhost 7634 | cut -c23-24 ;}C
  ${color4}Vcore: ${color5}${i2c 9191-0290 in 0}V ${alignr}${color4}${exec nc localhost 7634 | cut -c29-36 ;}: ${color5}${execi 300 nc localhost 7634 | cut -c50-51 ;}C
  ${color4}MB Temp: ${color5}${i2c 9191-0290 temp 3}C ${alignr}${color4}${exec nc localhost 7634 | cut -c56-63 ;}: ${color5}${execi 300 nc localhost 7634 | cut -c77-78 ;}C
  ${color4}MB Fan Spd: ${color5}${i2c 9191-0290 fan 3} rpm${alignr}${alignr}${color4}${exec nc localhost 7634 | cut -c83-90 ;}: ${color5}${execi 300 nc localhost 7634 | cut -c112-113 ;}C
${color7}MEMORY / DISK ${hr 2}$color
  ${color4}RAM: ${color3} $mem/$memmax ${color9}${membar 6}$color
  ${color4}HD IO: ${color3}${diskio} ${alignr}${color #0077ff}${color #0077ff}${diskiograph 6,200 000000 0077ff}${color}
  ${color4}Swap: ${color3}$swapperc%${color6} ${swapbar 6}$color
${color7}FILE SYSTEM (Free / Total) ${hr 2}$color
  ${color4}/root: ${color5}${fs_used /} / ${fs_free /} ${alignr}${color lightblue}${fs_bar 6,100 /}${color}
  ${color4}/home: ${color5}${fs_used /home} / ${fs_free /home} ${alignr}${color lightblue}${fs_bar 6,100 /home}${color}
  ${color4}/var: ${color5}${fs_used /var} / ${fs_free /var} ${alignr}${color lightblue}${fs_bar 6,100 /var}${color}
  ${color4}/usr/local: ${color5}${fs_used /usr/local} / ${fs_free /usr/local} ${alignr}${color lightblue}${fs_bar 6,100 /usr/local}${color}
  ${color4}/data: ${color5}${fs_used /data} / ${fs_free /data} ${alignr}${color lightblue}${fs_bar 6,100 /data}${color}
  ${color4}/data2: ${color5}${fs_used /data} / ${fs_free /data2} ${alignr}${color lightblue}${fs_bar 6,100 /data2}${color}
  ${color4}WinXp C:  ${color5}${fs_used /media/C} / ${fs_free /media/C}${alignr}${color green}${fs_bar 6,100 /media/C}${color}
  ${color4}WinXp D:  ${color5}${fs_used /media/D} / ${fs_free /media/D}${alignr}${color green}${fs_bar 6,100 /media/D}${color}
  ${color4}WinXp E:  ${color5}${fs_used /media/E} / ${fs_free /media/E}${alignr}${color green}${fs_bar 6,100  /media/E}${color}
  ${color4}WinXp F:  ${color5}${fs_used /media/F} / ${fs_free /media/F}${alignr}${color green}${fs_bar 6,100  /media/F}${color}
  ${color4}WinXp G:  ${color5}${fs_used /media/G} / ${fs_free /media/G}${alignr}${color green}${fs_bar 6,100  /media/G}${color}
  ${color4}WinXp L:  ${color5}${fs_used /media/L} / ${fs_free /media/L}${alignr}${color green}${fs_bar 6,100  /media/L}${color}
${color7}PROCESSES ${hr 2}$color
  ${color purple} PROC NAME              ${alignr}PID     CPU%    MEM%$color
   ${color4}${top name 1} ${alignr}${color5}${top pid 1}   ${top cpu 1}    ${top mem 1}${color}
   ${color4}${top name 2} ${alignr}${color5}${top pid 2}   ${top cpu 2}    ${top mem 2}${color}
   ${color4}${top name 3} ${alignr}${color5}${top pid 3}   ${top cpu 3}    ${top mem 3}${color}
   ${color4}${top name 4} ${alignr}${color5}${top pid 4}   ${top cpu 4}    ${top mem 4}${color}
${color7}NETWORK ${color2}(eth1 ${addr eth1} / br0 ${addr br0}) ${color7}${hr 2}$color
  ${color4}Down: ${color Red}${downspeedf eth1}${color} k/s ${alignr}${color4}Up: ${color Red}${upspeedf eth1}${color} k/s
  ${color black}${downspeedgraph eth1 15,100 ff0000 0000ff} ${alignr}${color black}${upspeedgraph eth1 
  15,100 0000ff ff0000}$color
  ${color4}Total: ${color5}${totaldown eth1} ${alignr}${color4}Total: ${color5}${totalup eth1}
  ${color4}Inbound: ${color5}${tcp_portmon 1 32767 count}${color4} ${alignc}Outbound: ${color5}${tcp_portmon 32768 61000 count}  ${color4}${alignr}Total: ${color5}${tcp_portmon 1 65535 count}
${color7}LOGGING ${hr 2}$color
  ${color5}${execi 30 tail -n3 /var/log/messages | fold -w50}
${color7}WEATHER${hr 2}$color
${color2}Leesburg, VA: 
${color2}Current: ${color5}${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 M CC}   ${color2}Temp: ${color5}${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I LT} ${color2}  Precip: ${color5}${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I PC}${color2}   
Humidity: ${color5}${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I HM} ${color2}   Winds: ${color5}${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I WS} ${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I WD}
${color5}${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 M DW}    ${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 M DW D 1 5 5}
${font Weather:size=36}${color2}${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 M WF D 0 5}${font :size=8}
${color2}Hi:${color5} ${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I HT D 0}        ${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I HT D 1 5 11}
${color2}Lo${color5} :${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I LT N 0}        ${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I LT N 1 5 11}

```

Best, 
Dave

---

### Post by kaivalagi on 2008-04-19
> **dccrens said:**
> Finally finished! Thanks to all of you for a great thread and a great script. Here is my conkyrc and a screen shot.

```

${execi 3600 python ~/Scripts/conkyForecast.py USVA0427 I WS}

```

Best, 
Dave

Hi Dave, I just noticed the calmmph for wind speed on your screenshot...looks like the imperial output can be in words, is it always like this or can there be actual wind speeds output?

Just trying to figure out how best to fix things :)

Cheers

---

### Post by mokkurkalve on 2008-04-19
> **kaivalagi said:**
> Hi Dave, I just noticed the calmmph for wind speed on your screenshot...looks like the imperial output can be in words, is it always like this or can there be actual wind speeds output?

Hello! I noticed this with metric output
${execi 3600 python ~/.scripts/weather/conkyForecast.py NOXX0004 M WS}
will output calmkph if the string sent are a text string. This probably only happens with the
condition "calm" or 0kph. My output right  now here are: 6kph

A different issue:
${execi 3600 python ~/.scripts/weather/conkyForecast.py NOXX0004 M WD}
outputs: 190
I thought it should be a textual representaition of the wind direction like S or NW or NNW or SE etc.
"190" doesn't tell *me* much about where it's blowing from...  ;)

Thanks for good work BTW!

---

### Post by dccrens on 2008-04-19
kaivalagi,

Not sure on the wind. We've had calm/no wind the last day or two. I will watch it and see what happens. 

Dave

---

### Post by dccrens on 2008-04-19
kaivalagi,

On the wind output I can't get any other reading other than calmkph or calmmph using either Imperial or Metric. I tried plugging in all differrent locations from Barrow, to Miami, to Kuwait City, to Honolulu. All come back the same...

Dave

---

### Post by kaivalagi on 2008-04-19
> **mokkurkalve said:**
> Hello! I noticed this with metric output
${execi 3600 python ~/.scripts/weather/conkyForecast.py NOXX0004 M WS}
will output calmkph if the string sent are a text string. This probably only happens with the
condition "calm" or 0kph. My output right  now here are: 6kph

I'll see if I can add a isnumeric check before applying a kph to the text, that should sort it

> **mokkurkalve said:**
> 
A different issue:
${execi 3600 python ~/.scripts/weather/conkyForecast.py NOXX0004 M WD}
outputs: 190
I thought it should be a textual representaition of the wind direction like S or NW or NNW or SE etc.
"190" doesn't tell *me* much about where it's blowing from...  ;)!
The 190 must be a bearing, I'll either add a degree symbol on the end or translate ranges of degrees to N, NW, NNE etc

I'll probably get this done over the next week or so...
[COLOR="Blue"]
Edit: I get compass bearings like NNE back for my location UKXX0103? That's just plain wierd...why do it one way for one location and another for another?[/COLOR]
[COLOR="Navy"]Edit2: NNE for forecast data (i.e. day number provided) but 240 for example when current conditions...I'll see what I can sort out...[/COLOR]
[COLOR="Red"]Edit3: The latest tar.gz attached above now converts bearing to NNE etc for current conditions :)[/COLOR]

> **mokkurkalve said:**
> 
Thanks for good work BTW

Glad I can provide something people find useful :)

---

### Post by kaivalagi on 2008-04-20
> **dccrens said:**
> kaivalagi,

On the wind output I can't get any other reading other than calmkph or calmmph using either Imperial or Metric. I tried plugging in all differrent locations from Barrow, to Miami, to Kuwait City, to Honolulu. All come back the same...

Dave

FIxed in the latest attachment ;)

---

### Post by TB2 on 2008-04-20
Uhm sorry if this has already been solved, but I suddenly get the following error when running your script:

python conkyForecast.py SZXX003 M CC 0

```
prepare_data:Unexpected error:  <type 'exceptions.IndexError'>
output_data:Unexpected error:  <type 'exceptions.IndexError'>
```

I played around with the script a few days ago and it was running fine, now I get these errors. It happens with all possible options and arguments I tried. When I run the script with incorrect arguments, the usage dialog displays fine.

Any idea on how to fix this?

---

### Post by kaivalagi on 2008-04-20
> **TB2 said:**
> Uhm sorry if this has already been solved, but I suddenly get the following error when running your script:

python conkyForecast.py SZXX003 M CC 0

```
prepare_data:Unexpected error:  <type 'exceptions.IndexError'>
output_data:Unexpected error:  <type 'exceptions.IndexError'>
```

I played around with the script a few days ago and it was running fine, now I get these errors. It happens with all possible options and arguments I tried. When I run the script with incorrect arguments, the usage dialog displays fine.

Any idea on how to fix this?

Did you download a new version of the script? There is a requirement with the current version to define day or night. If you are trying to use it with old conky config settings (old being more than 2 days old :) ) that might explain it

try this:

```
python conkyForecast.py SZXX003 M CC D 0
```

**A quick heads up**: because of the sheer number of arguments that can be used now I am currently rewriting the script to handle decent command line parameters. This should be finished today (pending tests).

Once done you will then need to call the script like this

```
python conkyForecast.py --location=SZXX003 --datatype=CC --startday=0
```

Things are changing rapidly with this script, but we should be in a good position with command line options shortly. Once I have finished today, the script usage should remain the same regardless of any newer functionality that's been added.

I suggest you get the script I will post this afternoon and adjust for that, you won't have troubles like this again then (fingers crossed)

Sorry for the inconvenience, nearly there :)

---

### Post by kaivalagi on 2008-04-20
**I will be posting into a new thread once the script is ready today**, there have been enough changes to warrant a fresh start with a new thread.

I plan to keep the script usage and download up-to-date with any bug fixes / enhancements I apply, at the top of the thread...

I'll link to the new thread from here (and at the top) when I have posted it....

Cheers

---

### Post by kaivalagi on 2008-04-20
[B][COLOR="Blue"]New script posted in new thread
[URL="http://ubuntuforums.org/showthread.php?p=4752373"]http://ubuntuforums.org/showthread.php?p=4752373
[/URL]
I'll keep an eye on this thread for a while, but I don't really want to support anything too old so please use the new script on the new thread wherever possible
Thanks[/COLOR][/B]

---

