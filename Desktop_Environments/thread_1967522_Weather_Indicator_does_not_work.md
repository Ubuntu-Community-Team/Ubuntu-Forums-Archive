---
title: "Weather Indicator does not work"
date: 2012-04-28
forum: Desktop Environments
---

### Post by blitzit on 2012-04-28
On Ubuntu 12.04, the Weather Indicator Applet gets installed successfully.

However, on clicking Add Locations, and on searching for a location (I am searching for New Delhi) the applet gets no results.

I am behind an institute proxy. Is this the reason Weather Indicator is not working? The applet does not have any settings regarding proxy so is there a possible work around?

---

### Post by nampat on 2012-04-28
Proxy might be the issue, because i just tried to install it myself and it is working fine. Try change the weather source from Yahoo to Google or vice versa.

---

### Post by blitzit on 2012-04-28
I tried reinstalling the applet, but it does not help. I have set a system-wide proxy setting and I am logged in through my browser.

I also realize, the OK button on the applet setting window is greyed out. I cannot confirm the settings I am entering. Does this need to be run as root?

---

### Post by lealcy on 2012-05-03
Same issue here. I'm certain that this is about the proxy.

---

### Post by lealcy on 2012-05-03
Report this bugs here:

[https://bugs.launchpad.net/ubuntu/+source/indicator-weather/+bug/835092](https://bugs.launchpad.net/ubuntu/+source/indicator-weather/+bug/835092)

---

### Post by chehmsoth on 2012-07-30
Under the Preferences menu in the General tab I changed the Weather Source radio button from Google to Yahoo and it started working again.

---

### Post by garyzw on 2012-07-31
Try my weather indicator instead--works much better

[http://ubuntuguide.net/weather-indicator-in-ubuntu-12-04-unity#comment-13079](http://ubuntuguide.net/weather-indicator-in-ubuntu-12-04-unity#comment-13079)

---

### Post by SirWeazel on 2012-07-31
Not sure if i can just add to your thread or not, but i also am having problems with this indicator. I'm able to find cities ok, but the indicator does not show the weather. All it displays is the orange icon, and when i click on the icon there is alot of grey blank space then below the space (where i think weather should be displayed) it says "forecasts, preferences, about, quit".

I installed the indicator applet from software center, running ubuntu 12.04 precise 64 bit with unity 3d, Weather Indicator 11.11.28 'Cloudy 9'

Any ideas?

---

### Post by yellabelly on 2012-08-02
I have the exact same problem that I'm trying to solve. Strange it worked fine on a 12.04 x64 laptop.

> **SirWeazel said:**
> Not sure if i can just add to your thread or not, but i also am having problems with this indicator. I'm able to find cities ok, but the indicator does not show the weather. All it displays is the orange icon, and when i click on the icon there is alot of grey blank space then below the space (where i think weather should be displayed) it says "forecasts, preferences, about, quit".

I installed the indicator applet from software center, running ubuntu 12.04 precise 64 bit with unity 3d, Weather Indicator 11.11.28 'Cloudy 9'

Any ideas?

---

### Post by yellabelly on 2012-08-02
I have it working now. 
A dependency was missing 
sudo apt-get install python-pywapi

it still wasn't working so I removed version 11.11.28 'Cloudy 9' and installed 
12.07.30 'Cloudy 10' from here 
[http://launchpadlibrarian.net/111494405/indicator-weather_12.07.30-0ubuntu1_all.deb](http://launchpadlibrarian.net/111494405/indicator-weather_12.07.30-0ubuntu1_all.deb)

I'm not sure exactly what made the difference but after these 2 actions it started working correctly.
Hope that helps.

---

### Post by lovevn on 2013-01-12
> **garyzw said:**
> Try my weather indicator instead--works much better

[http://ubuntuguide.net/weather-indicator-in-ubuntu-12-04-unity#comment-13079](http://ubuntuguide.net/weather-indicator-in-ubuntu-12-04-unity#comment-13079)
well, thank you very much. I try installing **weather indicator **many times, but it didn't work! :(
And I try **my-weather-indicator. **It's very good! 
one thanks! :)

---

### Post by Fitch on 2013-06-07
I installed a clean version of Ubuntu 12.04

I then installed the weather applet.
It hung when I put in accepted Edinburgh, Scotland, United Kingdom and pressed Apply

I did the two suggestions as above, and I have no proxy.

It always hangs when I put a location in.

Anobody with any other ideas?

---

