---
title: "Good weather (modifyed version) Not working"
date: 2008-05-08
forum: Desktop Environments
---

### Post by 127.0.0.1 on 2008-05-08
Hello i see most people with the Goodweather **Desklet** as the desklet dosen't retrive the weather. I've tried what this person suggested [http://ubuntuforums.org/showpost.php?p=4909608&postcount=2](http://ubuntuforums.org/showpost.php?p=4909608&postcount=2) and either i am not doing it right or it didn't work. Could some one help me please?

I am using this version of Goodweather: [http://gnome-look.org/content/show.php/Good+Weather+Mod-Small+%28gDesklets%29?content=72344](http://gnome-look.org/content/show.php/Good+Weather+Mod-Small+%28gDesklets%29?content=72344)

so the python file isn't were it is for the usual desklet.

---

### Post by garyedwardjohnston on 2008-05-08
gDesklets is a dead project.

Use screenlets.

[http://www.screenlets.org/index.php/Home](http://www.screenlets.org/index.php/Home)

---

### Post by sergks on 2008-05-09
You have to modify __init__.py file:

Go to: ~/.gdesklets/Sensors/GoodWeather and open the file __init__.py in gedit. Find the line 
WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
"%(weather_code)s?cc=*&dayf=5&prod=xoap&" \

and change it to:
WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
"%(weather_code)s?cc=*&dayf=5&prod=xoap&link=xoap& " \

This worked for me in Hardy.

---

### Post by 127.0.0.1 on 2008-05-10
> **sergks said:**
> You have to modify __init__.py file:

Go to: ~/.gdesklets/Sensors/GoodWeather and open the file __init__.py in gedit. Find the line 
WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
"%(weather_code)s?cc=*&dayf=5&prod=xoap&" \

and change it to:
WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
"%(weather_code)s?cc=*&dayf=5&prod=xoap&link=xoap& " \

This worked for me in Hardy.

I've tried that, it didn't work. Is the line supposed to look like this?

---

### Post by sergks on 2008-05-10
Sorry, in my case it looks like this: 

```

WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
                     "%(weather_code)s?cc=*&dayf=5&prod=xoap&link=xoap&" \
                     "par=1003832479&key=bb12936706a2d601"

```

But the last line may be different in your case. Also, there is no free space between x and oap& (Sorry, I had to post it as a code).

Try to reinstall your desklet and then modify the second line in the code above.

---

### Post by 127.0.0.1 on 2008-05-10
> **sergks said:**
> Sorry, in my case it looks like this: 

```

WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
                     "%(weather_code)s?cc=*&dayf=5&prod=xoap&link=xoap&" \
                     "par=1003832479&key=bb12936706a2d601"

```

But the last line may be different in your case. Also, there is no free space between x and oap& (Sorry, I had to post it as a code).

Try to reinstall your desklet and then modify the second line in the code above.

Yep that did it. Thanks man. :popcorn:

---

### Post by sergks on 2008-05-10
Ok. Good luck.

---

### Post by mlmondone on 2008-06-27
Hi,

I've been struggling all afternoon trying to get "GoodWeather" to work but this was the only thing that worked for me.  Thanks so VERY much...ML

---

### Post by rustic on 2008-10-07
Found this thread from a cross-link and first off, I'd like to say thank you for the desklet.  Secondly, I'd like to say thanks for the reference link.

Nice desklet.  I'm using the "small" variant.

It pleases me.

---

### Post by sanjayak on 2008-10-13
I got rid of the xoap parameter and it did work for me.

```

 WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
                     "%(weather_code)s?cc=*&dayf=5&" \
                     "par=1003832479&key=bb12936706a2d601"

```

---

### Post by arthur24b6 on 2008-10-29
This worked for for me. I put a tar ball of the good weather desklet with the modified xoap line <a href="http:24b6.net/files/good_weather_mod.tgz">here</a> since it was to big to attach here.

---

### Post by wmichaelb on 2009-01-30
Cutting and pasting this exact code worked for me in 64-bit Ibex as well. Thanks! This problem has been irritating me for a couple of months.

---

