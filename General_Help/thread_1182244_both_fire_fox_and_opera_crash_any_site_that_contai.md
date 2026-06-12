---
title: "both fire fox and opera crash any site that contains flash"
date: 2009-06-08
forum: General Help
---

### Post by nacho32 on 2009-06-08
I was having this problem of fire fox crashing on pages that had flash on them it freezes cpu goes to 100% then have to force shut down. So then I installed opera browser and it does the same thing, help 9.04 64 bit..

---

### Post by nacho32 on 2009-06-09
bump

---

### Post by ManiacDan on 2009-06-09
Have you tried uninstalling and reinstalling flash?  I use adobe-flashplugin 10.0.22.87-1

-Dan

---

### Post by Entropy_Sam on 2009-06-09
If you're using 64 bit Ubuntu, take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1176978](http://ubuntuforums.org/showthread.php?t=1176978). I'm going to try this out tonight, as I'm having similar problems.

---

### Post by nacho32 on 2009-06-09
> **ManiacDan said:**
> Have you tried uninstalling and reinstalling flash?  I use adobe-flashplugin 10.0.22.87-1

-Dan
yes I just tried that, the odd thing is is flash doesn't load on opera , loads in fire fox but still the same thing random freeze crash
I'm looking at [live radar weather page]("http://www.myfoxchicago.com/subindex/weather/weather_other2") and I have seen that thread that was posted but it seems to retain to just fire fox and talks about moving plug-ins into another folder, still would not solve my problem for opera as well. Hopefully a fix or patch will be issued soon, shrugs i might have to choose my windows boot on start up](*,)

---

### Post by Soul-Sing on 2009-06-09
using 64 bit? download the pre-release of adobe flash., unpack it on your Desktop:libflashplayer.so
```
cd Desktop
```
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```
```
sudo cp libflashplayer.so /usr/lib/opera/plugins
```

just uninstall "other" versions.

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz)
is the linkadress of the pre-release....

---

### Post by nacho32 on 2009-06-09
> **leoquant said:**
> using 64 bit? download the pre-release of adobe flash., unpack it on your Desktop:libflashplayer.so
```
cd Dekstop
```
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```
```
sudo cp libflashplayer.so /usr/lib/opera/plugins
```

just uninstall "other" versions.

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz)
is the linkadress of the pre-release....
I must be a tard it tells me no file or diretory exist

---

### Post by Soul-Sing on 2009-06-09
try it again, I made a typo....

---

### Post by 101011010010 on 2009-06-09
On the Adobe Labs website it says for 64 bt to put the libflashplayer.so to ~/.mozilla/plugins. [http://labs.adobe.com/technologies/f...html#install](http://labs.adobe.com/technologies/f...html#install). I installed as they said and have had no probz.I hope this helps.

---

