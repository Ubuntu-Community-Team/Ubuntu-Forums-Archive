---
title: "OpenArena mosquito-like buzzing sound."
date: 2010-01-05
forum: Gaming &amp; Leisure
---

### Post by dragos240 on 2010-01-05
Hi,

Every time I open up openarena, I keep hearing this buzzing sound. Everything else works just fine, it's just when I open up openarena. I have no idea why this is happening. Either that or a mosquito enters my speaker every time I start the game up. Never happened before with other distros. Is it just karmic perhaps?

---

### Post by felious_fadger on 2010-01-05
u, k or x?

---

### Post by dragos240 on 2010-01-06
> **felious_fadger said:**
> u, k or x?

Ubuntu. With GNOME. I am suspecting that pulseaudio is the issue, it's been the issue before. And my other distros don't have this problem, they don't have pulseaudio. I'm not 100% sure if it's the issue, but it's happenened before.

---

### Post by guitar_man on 2010-01-07
I had the same experience....

---

### Post by dragos240 on 2010-01-08
Uh. Hi??

---

### Post by rahuroon on 2010-01-28
any solutions please? i am a new user of ubuntu/linux...and all these hiccups are pushing me to switch towards windows again.

---

### Post by rahuroon on 2010-01-28
For all those who are facing sound problems.....(refer above posts)
after 3 hours i found out .....pulseaudio is the culprit..remove it and install esound in place of it:p:p

i followed this

[http://ubuntuforums.org/showthread.php?t=1313253](http://ubuntuforums.org/showthread.php?t=1313253)

But the new problem is no sound controller on desktop now:icon_frown:..i dont know how to control sound know

---

### Post by duracell999 on 2010-01-28
I had a similar problem with Smokin Guns (a quake3 mod). After applying wayfarers fix I managed to get rid of the buzzing noise.
[http://www.smokin-guns.net/viewtopic.php?t=1981&sid=3affbe432a397c913efd37d2e85cb87b](http://www.smokin-guns.net/viewtopic.php?t=1981&sid=3affbe432a397c913efd37d2e85cb87b)
Hope that helps

---

### Post by dragos240 on 2010-01-28
Well since I don't use ubuntu any longer, there is no need. Glad the issue is fixed rahuroon.

---

### Post by pirog on 2010-02-08
for those who don't want to remove pulseaudio (skype, home digital systems, etc.) try installing libsdl1.2debian-pulseaudio (instead of libsdl1.2debian-all), Gnome Alsamixer and pulseaudio device chooser.

In GnomeAlsamixer i found an option "Digital" - turned it down and scratching noise disappeared.

Pulseaudio chooser, let's you set up skype in Karmic (alsa+pulseaudio)

As far as my gaming is concerned, I tried to play some music and openarena simultaneously. Openarena crashed every time I tried to close it and whenever i pressed "w" i had this crackling noise coming back on, after my game sounds would disappear altogether. i looked up the settings in the system menu (of openarena) and set quality sound from "high" to "low" - now everything works: no scratching sounds, sound does not disappears after two minutes playing the game and openarena stopped crashing on every exit!

hope it helps.

---

