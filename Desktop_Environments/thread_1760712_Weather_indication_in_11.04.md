---
title: "Weather indication in 11.04"
date: 2011-05-17
forum: Desktop Environments
---

### Post by raunhar on 2011-05-17
Till 10.10 , Ubuntu would show the temperature and sunrise/sunsite time, when enabled from Time Settings.
There is no such thing in Ubuntu 11.04
Can I install it externally.

---

### Post by Frogs Hair on 2011-05-17
I'm using the one at the link and there is an application in the synaptic package manager called indicator-weather . I have tried them both and prefer the one at the link , but it does not include sunrise time , I think indicator weather does.   [http://www.omgubuntu.co.uk/2011/05/my-weather-indicator-location-selection-gets-revamped/](http://www.omgubuntu.co.uk/2011/05/my-weather-indicator-location-selection-gets-revamped/)

---

### Post by Frogs Hair on 2011-05-17
I use this Opera Widget for moon phase/sun .

---

### Post by raunhar on 2011-05-17
Tried to install it.
Added the ppa to list.
On typing My Weather Indicator into the search box, nothing showed up.

---

### Post by NormanFLinux on 2011-05-17
Once you install weather indicator, you have to launch the application to install it in the global menu panel.

---

### Post by divyenduv on 2011-05-27
I am also facing same problem. I believe in 11.04 release, this option is disabled by the team. Any one ??

---

### Post by raunhar on 2011-05-27
I installed My weather Indicator.
But everytime I have to manually start it. Auto start is not working.

---

### Post by maverick280857 on 2011-05-27
Have a look at [https://launchpad.net/weather-indicator](https://launchpad.net/weather-indicator). You can get this from the repos.

Alternately, get 'screenlets' and set up the weather-screenlet.

Another option is to use cairo-dock..it comes with a weather widget.

---

### Post by maverick280857 on 2011-05-27
> **raunhar said:**
> I installed My weather Indicator.
But everytime I have to manually start it. Auto start is not working.

You'll have to create a weatherindicator.desktop file in $HOME/.config/autostart/, which looks like this:

```
[Desktop Entry]
Type=Application
Exec=/path_to_prog/progname
Hidden=false
X-GNOME-Autostart-enabled=true
Name[en_US]=progname
Name=progname
Comment[en_US]=Description
Comment=Description

```

You'll need to replace path_to_prog and progname appropriately of course.

Logout and log back in.

---

### Post by rmstock2 on 2011-06-25
This has got to be the biggest gig Google and Yahoo pulled on NOAA.
Vadim Rutkovsky, although admitting (#TODO: Get noaa id from geonames service)
still hasn't implemented a hookup to weather.noaa.gov  :

[IMG]http://img98.imageshack.us/img98/5843/vadimrutkovskyweatherpr.jpg[/IMG]

[http://img98.imageshack.us/img98/5843/vadimrutkovskyweatherpr.jpg](http://img98.imageshack.us/img98/5843/vadimrutkovskyweatherpr.jpg)

NOAA stands for National Oceanic and Atmospheric Administration by the US
Goverment. These people gather weather intelligence to save lives. So implement
this Weather DATA source. Vadim seems to take his time.

---

