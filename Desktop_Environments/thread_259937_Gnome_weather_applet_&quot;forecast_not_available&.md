---
title: "Gnome weather applet: &quot;forecast not available&quot;"
date: 2006-09-18
forum: Desktop Environments
---

### Post by allanlewis on 2006-09-18
Hi,

I use the Gnome panel weather applet and I split my time between Liverpool and Leeds (both in the UK). (Leeds is listed as "Leeds/Bradford", persumably because the weather report comes from the weather station at Leeds/Bradford Airport.)

When I am in Liverpool, I can get both the current conditions and the detailed forecast, but in Leeds, only the current conditions. Why is this? On uk.weather.com I can get a [detailed forecast]("http://uk.weather.com/weather/hourbyhour/UKXX0078") for Leeds - is this not where the applet gets its information?

Thanks in advance!

---

### Post by orb9220 on 2006-09-18
I believe that the weather applet only uses weather.com and not uk.weather.com but am not postive on that.

If somebody could post the config file for this applet where we can verify where it is connecting to.

---

### Post by artinla on 2006-09-18
If you are talking about the gdesklet such as the sidecandy weather app, most of them use yahoo.com weather but rarely work.

I finally just gave up trying to get it going..  Hope you find an answer.

---

### Post by allanlewis on 2006-09-18
> **orb9220 said:**
> I believe that the weather applet only uses weather.com and not uk.weather.com but am not postive on that.

If somebody could post the config file for this applet where we can verify where it is connecting to.

Ok, so if it uses the US site, then surely it wouldn't give me any information? As I said, it gives me current conditions, i.e. temperature, humidity, pressure, wind, but it just won't give me the detail. And (again, as I said above ](*,) ) it works fine for Liverpool!

If anyone knows where the config for this applet is stored then I'll post it myself, but I can't find any man pages for it. (I looked under gnome-panel and a tried a couple of other things but couldn't get anywhere.)

[QUOTE=artinla]If you are talking about the gdesklet such as the sidecandy weather app...[/QUOTE]

No, I'm not.

---

### Post by orb9220 on 2006-09-18
This is the link for leeds [http://uk.weather.com/weather/local/UKXX0078](http://uk.weather.com/weather/local/UKXX0078)
"                liverpool [http://uk.weather.com/weather/local/UKXX0083](http://uk.weather.com/weather/local/UKXX0083)

I did a detail comparsion which the only difference I could see was  liverpool had two lines descripter for wind and that's it. Everything else looked exactly the same.

Sorry I couldn't see anything obvious.

---

### Post by allanlewis on 2006-09-18
> **orb9220 said:**
> <snip>
Sorry I couldn't see anything obvious.

Thanks for your help.
Has anyone else got any ideas?

---

### Post by crossedout on 2006-09-18
gweather is located under /usr/share/gnome-applets/gweather.

Hope That helps.

-Xout

---

