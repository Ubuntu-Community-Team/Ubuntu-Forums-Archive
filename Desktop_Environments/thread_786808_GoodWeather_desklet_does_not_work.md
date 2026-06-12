---
title: "GoodWeather desklet does not work"
date: 2008-05-08
forum: Desktop Environments
---

### Post by sergks on 2008-05-08
After few updates in Hardy my GoodWeather desklet stopped working. It's always showing 'Loading' sign. Can somebody help me?
Also (it might be related), Gnome clock applet does not show weather but weather applet is working fine.

---

### Post by sergks on 2008-05-08
Thanks to Kevbert post located here: [http://ubuntuforums.org/showpost.php?p=4909608&postcount=2]("http://ubuntuforums.org/showpost.php?p=4909608&postcount=2") I found the solution.

Go to: ~/.gdesklets/Sensors/GoodWeather and open the file __init__.py in gedit. Find the line 
WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
                  "%(weather_code)s?cc=*&dayf=5&prod=xoap&" \
                  
and change it to:
WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
                     "%(weather_code)s?cc=*&dayf=5&prod=xoap&link=xoap&" \

---

### Post by mister_p_1998 on 2008-05-08
> **sergks said:**
> Thanks to Kevbert post located here: [http://ubuntuforums.org/showpost.php?p=4909608&postcount=2]("http://ubuntuforums.org/showpost.php?p=4909608&postcount=2") I found the solution.

Go to: ~/.gdesklets/Sensors/GoodWeather and open the file __init__.py in gedit. Find the line 
WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
                  "%(weather_code)s?cc=*&dayf=5&prod=xoap&" \
                  
and change it to:
WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
                     "%(weather_code)s?cc=*&dayf=5&prod=xoap&link=xoap&" \

Works on Hardy, doesnt work on Dapper. any clue why?

---

### Post by sergks on 2008-05-08
> **mister_p_1998 said:**
> Works on Hardy, doesnt work on Dapper. any clue why?

Sorry. Do not know why, do not have Dapper installed. Dapper might have different version of gDesklets. But the idea is the same. Weather.com recently changed the access to the database and weather desklets stoped working. You have to find the file with weather source and change it.

---

### Post by mister_p_1998 on 2008-05-12
> **sergks said:**
> Sorry. Do not know why, do not have Dapper installed. Dapper might have different version of gDesklets. But the idea is the same. Weather.com recently changed the access to the database and weather desklets stoped working. You have to find the file with weather source and change it.

Working now on Dapper, I just pasted the end of the changes onto my file rather than pasting the whole entry in as new. looked like a formatting problem.

---

### Post by AndréPayão on 2008-05-21
Here i edited like this, and worked :

"http://xoap.weather.com/weather/local/" \
"%(weather_code)s?cc=*&dayf=5&prod=xoap&link=xoap&" \
"par=1003832479&key=bb12936706a2d601"

i found solution in this topic : [http://ubuntuforums.org/showthread.php?t=784053&highlight=weather](http://ubuntuforums.org/showthread.php?t=784053&highlight=weather)

---

### Post by The Nothing on 2008-06-16
Adding link=xoap& worked like a charm .. thanks :)

---

### Post by Carl_Barks on 2008-07-10
worked like a charm! Thnx guys!

---

### Post by MFelkins on 2008-07-12
> **sergks said:**
> Thanks to Kevbert post located here: [http://ubuntuforums.org/showpost.php?p=4909608&postcount=2]("http://ubuntuforums.org/showpost.php?p=4909608&postcount=2") I found the solution.

Go to: ~/.gdesklets/Sensors/GoodWeather and open the file __init__.py in gedit. Find the line 
WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
                  "%(weather_code)s?cc=*&dayf=5&prod=xoap&" \
                  
and change it to:
WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
                     "%(weather_code)s?cc=*&dayf=5&prod=xoap&link=xoap&" \
Worked for me. But, as I am a noob at this, it took me a while to find the file. I did not realize that it would be under my profile and hidden. I found it here:

/home/mike/.gdesklets/Sensors/GoodWeather

Your milage may very. How do I change the background on the applets?

---

### Post by matiasborra on 2008-11-22
I just installed Ubuntu 8.10 (Intrepid Ibex) and I made it work with the modification proposed:
    WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
                     "%(weather_code)s?cc=*&dayf=5&prod=xoap&link=xoap&" \
Thanks.

---

### Post by niedxwiedx on 2008-12-29
Does not work for me. (Ubuntu 8.04, gDesklets 0.35.4). I have obtained location code for my city (also tried different codes), and modified WEATHER_SOURCE in __init__.py file. And i still see "N/A loading". Any clues?:confused:

---

### Post by sdtootle on 2009-02-12
WEATHER_SOURCE = "http://xoap.weather.com/weather/local/" \
                     "%(weather_code)s?cc=*&dayf=5&link=xoap&" \
                     "prod=xoap&par=1003832479&key=bb12936706a2d601" \

This worked for me.  if you are in a US area, just put in the zip code.  that worked for me.

---

### Post by labinnsw on 2009-06-13
Thanks. This worked after deleting some spaces.

Change from:
> "%(weather_code)s?cc=*&dayf=5&prod=xoap&link=xoap& " \
to
> "%(weather_code)s?cc=*&dayf=5&prod=xoap&link=xoap&"\

---

### Post by niedxwiedx on 2009-09-19
I confirm it's now working, i had an error in my __init__.py file:)

---

