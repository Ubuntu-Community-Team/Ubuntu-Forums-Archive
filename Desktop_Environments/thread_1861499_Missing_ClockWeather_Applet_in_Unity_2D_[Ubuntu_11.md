---
title: "Missing Clock/Weather Applet in Unity 2D [Ubuntu 11.10]"
date: 2011-10-15
forum: Desktop Environments
---

### Post by Arkitekt on 2011-10-15
Just upgraded to Ubuntu 11.10, since I can't seem to install netbook-launcher-efl anymore since it is been removed I have settled for Unity 2D on my netbook. 

All of my other applets are still in the top right: Tomboy Notes, Battery, Wireless, Sound, etc. But I am missing the clock with weather applet that has always been there before. How can I add this? right clicking the panel doesn't allow my to add indicators or move them around like I could before. I also would like to get rid of the mail icon looking indicator.

---

### Post by Krytarik on 2011-10-15
> **Arkitekt said:**
> I am missing the clock with weather applet that has always been there before. How can I add this?
There is no unified clock/weather indicator available for Unity, afaik.
But you can add the stand-alone "Weather Indicator":

[http://www.tuxgarage.com/2011/05/weather-indicator-for-unity.html](http://www.tuxgarage.com/2011/05/weather-indicator-for-unity.html)

> **Arkitekt said:**
> right clicking the panel doesn't allow my to add indicators or move them around like I could before.
Re-arranging panel items is not exactly as easy as in classic Gnome.
But I think this method applies to Unity 2D, too:

[http://www.tuxgarage.com/2011/06/re-arrange-appindicators-in-ubuntu.html](http://www.tuxgarage.com/2011/06/re-arrange-appindicators-in-ubuntu.html)

> **Arkitekt said:**
> I also would like to get rid of the mail icon looking indicator.
Therefore, just remove the package "indicator-messages":
```
sudo apt-get purge indicator-messages
```Hope that helps a bit!

---

### Post by Arkitekt on 2011-10-15
That actually helps quite a bit :D thanks. I managed to figure out how to get the DateTime indicator to show on the panel, in the process of adding a weather indicator now.

---

### Post by menonrb on 2011-10-16
How did you get the DateTime indicator to show up? Having the same problem. Thanks.

---

### Post by Swagman on 2011-10-16
Many thanks for that from me as well... Gradually fettling 11:10 into an acceptable fashion.

---

### Post by williammanda on 2011-10-16
All I had to do was use the software center to install for 11.10. Nice app!

---

### Post by Krytarik on 2011-10-16
> **williammanda said:**
> All I had to do was use the software center to install for 11.10. Nice app!
Oh, yeah, by now Weather Indicator is also in the official repos of both Natty 11.04 and Oneiric 11.10. So, I've just updated the post I linked to earlier. Thanks for the hint! :P

---

### Post by rahaman.naik on 2011-10-21
Even after i installed the indicator-datatime and removing the indicator-messages, the clock is still missing :(. Can one tell me what went wrong ?

---

