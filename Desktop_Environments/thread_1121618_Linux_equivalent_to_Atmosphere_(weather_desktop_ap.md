---
title: "Linux equivalent to Atmosphere (weather desktop application)"
date: 2009-04-10
forum: Desktop Environments
---

### Post by Rincevent on 2009-04-10
Hello,

I am looking for a Linux equivalent of this Mac application:
[http://creativebits.org/my_dream_app_winner_atmosphere](http://creativebits.org/my_dream_app_winner_atmosphere)

I have found this application : [http://mundogeek.net/weather-wallpaper/](http://mundogeek.net/weather-wallpaper/)

But it's very basic compared to Atmosphere.

Regards,

Rince.

---

### Post by Vadi on 2009-04-10
I think the closest equivalent would be to have a widget that does this. But then again I didn't hear about weather-wallpaper before either.

---

### Post by linuxuser21 on 2009-04-10
> **Vadi said:**
> I think the closest equivalent would be to have a widget that does this. But then again I didn't hear about weather-wallpaper before either.
+1
I'm not sure about a weather equivalent either; however, if you want a widget or something like that, you could give Screenlets a try.

---

### Post by Roanoke on 2009-04-11
Start with conkyweather (in the repos, I believe). Write a bash script that gets the weather from conkyweather and picks an image for it. Then, replace the background image with the desired image (my bg image is always at ~/.background for convenience). Finally, have conky launch at startup to display weather things in text form.
I have no idea how to write this script (if statements and such). But it can be done.

---

### Post by Rincevent on 2009-04-12
Indeed, developing a screenlet or a script using conkyweather are good ideas. I was hoping that a similar application already exist. But, if not, I will try to develop something myself.

Thx,

Rince.

---

