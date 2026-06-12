---
title: "starcraft sound issue"
date: 2006-12-19
forum: Gaming &amp; Leisure
---

### Post by SigmaX6 on 2006-12-19
Hey i was wondering why i cannot get any sound in starcraft? do i need to install direct X via wine? to get them to work. I rem back in the day when i had a pemtium 90 and i refused to install the direct X for diablo and it ended up with me having no sound?

---

### Post by raid996 on 2006-12-29
Just solved the same exact problem with DD 6.06
- go "Application - Accessories - Alacarte menu editor"
- check the "Multimedia system selector" as visible in the "Preferences" tab
- go "System - Preferences - Multimedia..."
- select ALSA as output and input the exit
- open the terminal and type "winecfg"
- go to "audio" tab and select ALSA

Close and launch the game. It worked for me.
:mrgreen: 
This could be the first time I get to help some1 in this forum
:mrgreen: :mrgreen: :mrgreen: :mrgreen:

---

### Post by Mega_slayer on 2007-01-14
> **raid996 said:**
> Just solved the same exact problem with DD 6.06
- go "Application - Accessories - Alacarte menu editor"
- check the "Multimedia system selector" as visible in the "Preferences" tab
- go "System - Preferences - Multimedia..."
- select ALSA as output and input the exit
- open the terminal and type "winecfg"
- go to "audio" tab and select ALSA

Close and launch the game. It worked for me.
:mrgreen: 
This could be the first time I get to help some1 in this forum
:mrgreen: :mrgreen: :mrgreen: :mrgreen:

Thanks a lot I appreciate the help!

---

