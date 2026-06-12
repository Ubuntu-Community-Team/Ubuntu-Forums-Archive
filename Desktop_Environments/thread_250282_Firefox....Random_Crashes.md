---
title: "Firefox....Random Crashes"
date: 2006-09-03
forum: Desktop Environments
---

### Post by Hi-Teck on 2006-09-03
I am running Xubuntu 6.06 and randomly firefox will get pissed of can just close. I will reopen it use it for a bit.....Boom closes again...  Any idea anyone?

Thanks
Hi-Teck

---

### Post by someguyouknow on 2006-09-03
Mines use to do that. Found out it was due to some sound problem in flash.  
Is the site you are going to using flash?

---

### Post by Corp_Punisher on 2006-09-03
I had some issues with Firefox and plugins originally until I decided to do a reinstall and use EazyUbuntu. It fixed alot of the plugin issues including Java and Flash.

---

### Post by Hi-Teck on 2006-09-03
Flash or Java could have been being used during the first firefox crash...on the second, third, and forth.....just ebay, hotmail, etc.

What is EazyUbuntu?

---

### Post by aysiu on 2006-09-03
Try [this](http://ubuntuforums.org/showthread.php?t=103930).

---

### Post by Corp_Punisher on 2006-09-03
The Official Site:

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

This next link has some good info about EasyUbuntu as well:

[http://web.informbank.com/articles/technology/perfect-linux-desktop.htm](http://web.informbank.com/articles/technology/perfect-linux-desktop.htm)

It's also my understanding that EasyUbuntu works on Kubuntu as well as others, but I haven't researched that out myself.

---

### Post by vierranet on 2006-09-04
Are you hitting Flash sites when FF crashes?

It may be do to imbeded sound, Dapper at times drop the sound from Firefox & Flash and then poof it crashes.

here's a sound fix that may help.

sudo aptitude install alsa-oss
sudo gedit /etc/firefox/firefoxrc

FIREFOX_DSP=”aoss”

If that does'nt work, hit automatix for FF and flash.

it worked for me, less crashes anyways.

---

