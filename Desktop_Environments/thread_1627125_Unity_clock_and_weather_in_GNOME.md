---
title: "Unity clock and weather in GNOME?"
date: 2010-11-21
forum: Desktop Environments
---

### Post by TheWatcher000 on 2010-11-21
I have 10.10 Ubuntu (upgraded from 10.04), it's all nice and I like it, I use what I believe is called Ubuntu Desktop environment.
Here is a screenshot of my desktop, after clicking once on the clock: [http://img191.imageshack.us/i/desktopfhj.png/](http://img191.imageshack.us/i/desktopfhj.png/)

During the summer I read about a new weather forecast applet built in the clock that really caught my attention, here is a page about it: [http://www.webupd8.org/2010/07/install-weather-indicator-applet-with.html](http://www.webupd8.org/2010/07/install-weather-indicator-applet-with.html)

but when I try to run the commands

> ```
sudo add-apt-repository ppa:weather-indicator/weather-indicator-experimental && sudo apt-get update
sudo apt-get install indicator-weather
```After the first one I get:

```
dani@dani-laptop:~$ sudo add-apt-repository ppa:weather-indicator/weather-indicator-experimental && sudo apt-get update
Error reading https://launchpad.net/api/1.0/~weather-indicator/+archive/weather-indicator-experimental: HTTP Error 404: Not Found
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
dani@dani-laptop:~$ 
```

I really would like to have this clock/weather indicator, can anyone  help me to make it work? I've been trying to do it for months now but I fail hard apparently..

---

### Post by koleoptero on 2010-11-22
It looks like it was dropped and is not developed anymore. It was created because 10.10 would have a simplified clock without a calendar and weather, but they kept the classic one. I can't find it anywhere with several google searches :(

---

### Post by TheWatcher000 on 2010-11-25
bump because I hope someone knows otherwise

---

### Post by Frogs Hair on 2010-11-25
This is all I could find , looks like it has been inactive since July.
[https://launchpad.net/weather-indicator](https://launchpad.net/weather-indicator)

---

### Post by grege on 2010-11-26
Right click on the clock and in preferences set your location.

Then you will get a read out of the temperature and if you mouse over you will get current conditions.

Another option is to right click on the top toolbar and add an applet. Scroll down to the bottom of the list and you will find "Weather"

Neither are as fancy as the one you are after, but they are easily installed.

---

### Post by TheWatcher000 on 2010-11-26
> **grege said:**
> Right click on the clock and in preferences set your location.

Then you will get a read out of the temperature and if you mouse over you will get current conditions.

Another option is to right click on the top toolbar and add an applet. Scroll down to the bottom of the list and you will find "Weather"

Neither are as fancy as the one you are after, but they are easily installed.

I already have that but thanks. My old laptop only supports 1024 x 768 so I hoped to make more room on the upper panel.

---

### Post by FelixTheBunny on 2011-04-30
how do i get this gnome wheather calendar world time applet in natty narwhale 11.04.  i think its a great applet...hoovering with the mouse and i see my weather, clicking shows me world time with sun position (talking with people all over the world..great help) . sorry fo hijacking this thread but its exactly what i seek but, well opposite direction

---

### Post by Frogs Hair on 2011-04-30
Hi and welcome ,

It looks like this project may have become active again there is tar.gz file from 2-12-2011 at the link . I don't if it would work in Unity or Classic Gnome on 11.04 .  [https://launchpad.net/weather-indicator](https://launchpad.net/weather-indicator)

---

### Post by FelixTheBunny on 2011-05-01
thanks for your answer but, its not what i am looking for. i want the exact behaviour of the maverick meerkat clock including the visual presentation shown here [http://img191.imageshack.us/i/desktopfhj.png/](http://img191.imageshack.us/i/desktopfhj.png/). i dont know much about this all, but if there is a way to extract the clock from a meerkat build i would do it since i have a nother PC running 10.10

PS: sorry i mistakenly overread your doubt about its working. sorry again many times. well actually it works but as a seperate applet which is not satisfying. i cant believe they made something working good and fine be broken in the end.

---

### Post by mmfjr on 2011-05-28
> **FelixTheBunny said:**
> thanks for your answer but, its not what i am looking for. i want the exact behaviour of the maverick meerkat clock including the visual presentation shown here [http://img191.imageshack.us/i/desktopfhj.png/](http://img191.imageshack.us/i/desktopfhj.png/). i dont know much about this all, but if there is a way to extract the clock from a meerkat build i would do it since i have a nother PC running 10.10

PS: sorry i mistakenly overread your doubt about its working. sorry again many times. well actually it works but as a seperate applet which is not satisfying. i cant believe they made something working good and fine be broken in the end.
It is still available in the Gnome desktop if you select Ubuntu Classic when you log in.

---

### Post by FelixTheBunny on 2011-07-21
thanks for that answer too but this is STILL not the same applet. the unity clock doesnt show weather...i need to install the weather applet additionally but it is NOT the same. to me the weather/clock applet is a very good all in one solution. isnt there a way to extract that thing from a 10.10 installation and put it in my 11.04 installation?

---

### Post by Frogs Hair on 2011-07-21
```
sudo apt-get indicator-weather
```

You can try this PPA , I like it much better than the option above . when  either is installed they will have to be stared from dash . I think indicator weather will appear after restart  . [http://www.omgubuntu.co.uk/2011/05/my-weather-indicator-adds-sun-and-moon-info-feels-like-temp-and-more-in-latest-update/](http://www.omgubuntu.co.uk/2011/05/my-weather-indicator-adds-sun-and-moon-info-feels-like-temp-and-more-in-latest-update/)

PPA instructions :

sudo add-apt-repository ppa:atareao/atareao && sudo apt-get update

sudo apt-get install my-weather-indicator

---

### Post by FelixTheBunny on 2011-07-26
> **Frogs Hair said:**
> ```
sudo apt-get indicator-weather
```You can try this PPA , I like it much better than the option above . when  either is installed they will have to be stared from dash . I think indicator weather will appear after restart  . [http://www.omgubuntu.co.uk/2011/05/my-weather-indicator-adds-sun-and-moon-info-feels-like-temp-and-more-in-latest-update/](http://www.omgubuntu.co.uk/2011/05/my-weather-indicator-adds-sun-and-moon-info-feels-like-temp-and-more-in-latest-update/)

PPA instructions :

sudo add-apt-repository ppa:atareao/atareao && sudo apt-get update

sudo apt-get install my-weather-indicator

thanks again for your answer, i allready installed weather indicator applet(1-2 hours after installing 11.04). my problem is not having ANY weatherindicator i want THAT ubuntu 10.10 weather&clock app. whick shows calender, weather info and sun-lit earth. [IMG]http://ubuntuguide.net/wp-content/uploads/2010/11/time_weather1.png[/IMG] 
to me this thing is superior. minimized form shows weather and clock...ok..but maxed out you see different locations etc on a glance. weather and time for different places and this mini map. i am talking to people from different places on earth, friends and family are in different timezones etc. this thing was great looking up their time etc.

---

### Post by Frogs Hair on 2011-07-26
> **FelixTheBunny said:**
> thanks again for your answer, i allready installed weather indicator applet(1-2 hours after installing 11.04). my problem is not having ANY weatherindicator i want THAT ubuntu 10.10 weather&clock app. whick shows calender, weather info and sun-lit earth. [IMG]http://ubuntuguide.net/wp-content/uploads/2010/11/time_weather1.png[/IMG] 
to me this thing is superior. minimized form shows weather and clock...ok..but maxed out you see different locations etc on a glance. weather and time for different places and this mini map. i am talking to people from different places on earth, friends and family are in different timezones etc. this thing was great looking up their time etc.

I'm sure that packages is available somewhere , but weather it is compatible is the question . I don't understand the reason for changing it other than it caused a problem with the current version .

---

### Post by FelixTheBunny on 2011-08-02
thank you frogs hair. you see, this applet was really good and i miss it in 11.04. but if it isn&#8217;t available i have to live with it for now, except some smart guy adapts it to natty. thank you again.

---

### Post by Frogs Hair on 2011-08-02
I found this at Ask Ubuntu . [http://askubuntu.com/questions/29903/what-happened-to-the-weather-app-in-the-panel](http://askubuntu.com/questions/29903/what-happened-to-the-weather-app-in-the-panel)

---

