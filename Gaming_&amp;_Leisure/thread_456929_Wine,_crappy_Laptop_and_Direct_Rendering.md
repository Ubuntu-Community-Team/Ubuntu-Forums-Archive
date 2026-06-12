---
title: "Wine, crappy Laptop and Direct Rendering"
date: 2007-05-28
forum: Gaming &amp; Leisure
---

### Post by daynah on 2007-05-28
So, someone finally got the elitist kicked out of me. Someone being Blizzard announcing Starcraft 2. I then installed Starcraft and Broodwars on my desktop and laptop and then my boyfriend got me a WoW trial on my laptop (so long to install I haven't done it on my computer yet).

When wine is running on my laptop (intel video card), it constantly is whining in the background about this... libGL warning: 3D driver claims to not support visual 0x4b. My desktop, an nvidia, does not do this. Just a quick command to check if I have direct rendering, though I was sure I did (I'm running beryl on my laptop!), brings up the command again.

daynah@lapuntu:~$ glxinfo | grep direct
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes

Anyway, in Starcraft on the laptop, I'll be playing for maybe an hour and then the game will crash, and I assume wine too because my desktop is still wonky, not returned to it's prettiness. In Wow it does it just a few seconds after I enter the world. I lowered all of the settings to minimum, but... still crashes.

I know FF11 wouldn't run on my laptop but is there anyway to get around this? I like playing these games right next to people.

---

### Post by ShadowFlar3 on 2007-05-28
I hope you have followed a good guide to configuring wow on wine, such as:
[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine) ?

Further than that I don't think I can help you much. Error is obviously related to some conflict between libGL and video card driver.

---

### Post by daynah on 2007-05-28
I used the Ubuntu Wiki how to which, after looking, seems to be based off of the URL you gave. The edits that the guide said to put in the config.wtf though  made the game simply not run at all (couldn't change from 16 to 32) and made my system freeze, so I took them out and just tried to fiddle in game to get where you see above.

I'm now trying to install on my Windows partition to see if it's hardware or wine/linux drivers/whatever. Which means since I haven't used this partition in maybe a year, I have a bunch of updates to make sure they don't jump up and install in the middle of the warcraft installation. If it works, I'll post back saying it's okay. :)

---

