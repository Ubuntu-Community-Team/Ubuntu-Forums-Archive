---
title: "Sound playback does not work, system sounds do"
date: 2009-05-23
forum: General Help
---

### Post by k10chen on 2009-05-23
Hi Guys

I have a slight problem... when i log into ubuntu, i hear the classic login sound, but then when i play a video/music of anysort (on rythmbox, or VLC) the video would play but no sound would play (vlc) and no music would play at all (rhythmbox). 

sometimes the problems would be solved by a restart... but it doesnt always work. also, when i leave my computer on for a period of time, the sound would stop working again

any suggestions?

-K

---

### Post by khelben1979 on 2009-05-23
Are you using [Gnome]("http://en.wikipedia.org/wiki/Gnome_desktop") or [KDE]("http://en.wikipedia.org/wiki/Kde")?

The [Alsamixer]("http://en.wikipedia.org/wiki/Alsamixer") application is good for adjustment of the sound and I would advice you to install it if you haven't done so:

```
sudo apt-get install alsamixergui
```
installs the application with root priviliges.

[Alsaconf]("http://man-wiki.net/index.php/8:alsaconf") is another application where you have the possibility to change soundcard/soundchip and it can also be worth installing (I'm not sure if it's part of Ubuntu, though).

---

### Post by k10chen on 2009-05-23
Thanks! that worked out... somehow... i always think that its an application based problem, but it seems that adjusting the master volume works as well

Thanks for your help

-K

---

### Post by khelben1979 on 2009-05-23
Okay. :)

You also have gnome-alsamixer if you didn't like the GUI.

---

