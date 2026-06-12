---
title: "sdlmame, I can't win this fight"
date: 2010-02-20
forum: Gaming &amp; Leisure
---

### Post by dbldown768 on 2010-02-20
this is the second time I am trying to get MAME installed on my ubunutu 8.10 machine.  I mainly use if for xbmc but I really would like to get MAME running.

First off i installed the sdlmame that was in the repositories.  I then found this site ([http://sdlmame.wallyweek.org/](http://sdlmame.wallyweek.org/)) and updated the repositories to use this instead.  I was able to run sdlmame and find a rom I had located in my ~/.mame/roms folder.  But I can never get my original xbox controller to work with any of the games and could never get a coin entered into the game.

In doing so it appears that I remove my /etc/sdlmame folder.  This contained some mame.ini file and other config file that I dont recall.  I cannot get this folder to be recreated with the correct config files anymore - no matter if i use apt-get remove and install.  I can generate a mame.ini file using sdlmame -crateconfig but the other missing one appears to have corrected the display?

All I'd really like is to run a few roms and use my xbox controller.  If someone could help that would be great.  I have to imagine others are using a similar setup.  If this can't get fixed, i'll be back at this again in another 6 months when i try to get this working... uh so frustrating.

---

### Post by disturbedite on 2010-02-20
> **dbldown768 said:**
> In doing so it appears that I remove my /etc/sdlmame folder.  This contained some mame.ini file and other config file that I dont recall.  I cannot get this folder to be recreated with the correct config files anymore - no matter if i use apt-get remove and install.  I can generate a mame.ini file using sdlmame -crateconfig but the other missing one appears to have corrected the display?

i have sdlmame installed from packages on opensuse and i dont' have an /etc/sdlmame directory.

all my config files reside in ~/.mame

> **dbldown768 said:**
> All I'd really like is to run a few roms and use my xbox controller.  If someone could help that would be great.  I have to imagine others are using a similar setup.  If this can't get fixed, i'll be back at this again in another 6 months when i try to get this working... uh so frustrating.

sorry i can't help with this part. maybe sdlmame does not support xbox controllers, i don't know. i'd ask at the sdlmame forum. 

also, in general, maybe it would have been a better idea to ask these questions on the sdlmame forum instead of here.

---

