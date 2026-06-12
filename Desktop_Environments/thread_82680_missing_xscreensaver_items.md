---
title: "missing xscreensaver items"
date: 2005-10-27
forum: Desktop Environments
---

### Post by hoodwink on 2005-10-27
I have xscreensaver and xscreensaver-gl installed. What package(s) do I need to get the following that are missing when I run a demo?

Anemotaxis
BoxFit
Cosmos
Fireflies
Fireworkx
Goban
Intermomentary
jigsaw
MemScroller
Metaballs
Substrate
Substrate (circles)
VidWhacker
WebCollage
WebCollage (whacked)
Xaos
Xearth
Xfishtank
Xmountains
Xplanet
Xsnow

---

### Post by nbcthreat on 2005-12-29
Same question here. Synaptic says reallyslick is installed and they don't show up either.

---

### Post by asherlm on 2006-02-14
I just loaded rss-glx on my new install and I had to stop the xscreensaver process and run:

> /usr/bin/rss-glx_install.pl

The rss-glx screensavers were then in my list of available ones to run.

---

### Post by GeeZor on 2007-06-28
Guys,

try this:

sudo apt-get install xscreensaver-gl-extra xscreensaver-data xscreensaver xscreensaver-gl xscreensaver-data-extra

this will fix part of you problem.. haven't found how to installthe rest.. but when i do you'll be the first to know about it..:p

---

### Post by GeeZor on 2007-06-28
Okay, found it..

search for your package using ```
apt-cache search <name of screensaver>
```

jeffrey@REX:~$ ```
apt-cache search xearth
```
xplanet - render images of the earth
xplanet-images - day and night earth image maps for xplanet
xearth - Show a rotating earth on your X root window

so i just did a:
```
sudo apt-get install xplanet xplanet-images xearth
```
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xearth xplanet xplanet-images
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 1234kB of archives.
After unpacking 3158kB of additional disk space will be used.


and we where on the run again.. aint this fun guys :) :) :)  
Keep on rocking you box!

---

