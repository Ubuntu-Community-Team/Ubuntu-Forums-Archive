---
title: "audio problems"
date: 2005-12-07
forum: General Help
---

### Post by xShaDaBombx on 2005-12-07
im having problems hearing any music. I can hear frozen bubble and thats it. i cannot hear enemy territor either. help?:confused: :confused: :confused: :confused: :confused: :confused:

---

### Post by xShaDaBombx on 2005-12-07
a

---

### Post by 23meg on 2005-12-07
Noone can help without knowing what sound card, sound system (alsa/oss/esd) and applications you're having trouble with.

---

### Post by xShaDaBombx on 2005-12-07
[QUOTE=23meg]Noone can help without knowing what sound card, sound system (alsa/oss/esd) and applications you're having trouble with.[/QUOTE]
im sorry i am a total newb. my volume control preferences says C-media electronics cmi9738(oss mixer)  .
other info jsut ask. i listed the applications. i use xmms it doesnt work, streaming doesnt work, niether does enemy territory

---

### Post by Zimmer on 2005-12-07
Hi there ,
General hints.
Have you had a look at this guide to Enemy Territory.
Most of my problems, sound and video were sorted by going through this.
[https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)

There are many issues with sound, this helped mine, mostly, though there is a new unofficial guide for 5.10, though I don't have the link to hand..search this forum and you should find it.
[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)
Check the mixer settings to make sure one of the volume channels is not muted. Try unchecking 'Use sound for Events' in System>Preferences>sound and see if that helps..
When I had been through all that I found I could get sound in ET using the following tweaks:
Open a terminal session:

killall -9 esd
 ....I do not do that any more as I have re configured ESD as follows:-
 
 re configure esd in it's config file to release to other applications
 
 [esd] 
 auto_spawn=0
 spawn_wait_ms=100
 default_options= -terminate -nobeeps -as 2
 
 ..******....but I still type this in a Terminal to get it to produce sound....*******
 
 sudo sh -c 'echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss'
 
 **note the exact use of single and double quotes in the example above***

then type    et 
and it will run from the terminal and ,if you have problems, when you exit the game you will see the messages it generated and have a clue as to what might need sorting.

Best of luck
Zimmer

---

