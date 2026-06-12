---
title: "Changing desktop background based on weather"
date: 2009-03-09
forum: Desktop Environments
---

### Post by davidryder on 2009-03-09
Anyone know of any applications capable of doing this?

---

### Post by dusan.saiko on 2009-03-16
I think that is quite custom request, but I guess this can be done quite easily.

You can make a little script, which would:
- download the weather info from web, parse it, check for defined conditions (e.g. is it raining ?)
- select a background image according to the evaluation of the weather
- set the background using gconftool-2
- schedule the script in cron to run each lets say 20 minutes


example command for changing background (for Gnome)

gconftool-2 -t str --set /desktop/gnome/background/picture_filename /path/pic.png

---

### Post by amadeus266 on 2009-03-16
I think that this is a cool idea! I have seen other programs that change the wallpaper according to the time of day but not according to the weather. I'm interested and will be watching. I'll post here if I come up with any ideas.

---

### Post by blackened on 2009-03-16
The weather data can be had from weather.com, based on locale, in xml format. Go there and sign up for the SDK to get started.

---

### Post by binbash on 2009-03-16
Yup the weather data can be pulled from weather.com like conkyforecast and instead of daylight itis possible the changethe wallpaper via this.I am also looking for a script for this :)

---

### Post by kerry_s on 2009-03-16
you could try modifying the time of day script:
[http://joeamined.wordpress.com/2008/02/15/automatically-changing-wallpaper-relatively-to-daytime-in-ubuntu/](http://joeamined.wordpress.com/2008/02/15/automatically-changing-wallpaper-relatively-to-daytime-in-ubuntu/)

---

