---
title: "No Sound When Using Icon for WoW"
date: 2006-04-03
forum: Gaming &amp; Leisure
---

### Post by deboring21 on 2006-04-03
Ok, so I followed this guide ([http://ubuntuforums.org/showthread.php?t=120615](http://ubuntuforums.org/showthread.php?t=120615)) to install World of Warcraft. It works when I do the full command in terminal, but when I try to use the icon way, it runs but there is no sound... This is my command for the icon: wine /home/ryan/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -opengl. Please tell me how to fix it...
-Ryan

---

### Post by Sandlst on 2006-04-04
[QUOTE=deboring21]Ok, so I followed this guide ([http://ubuntuforums.org/showthread.php?t=120615](http://ubuntuforums.org/showthread.php?t=120615)) to install World of Warcraft. It works when I do the full command in terminal, but when I try to use the icon way, it runs but there is no sound... This is my command for the icon: wine /home/ryan/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -opengl. Please tell me how to fix it...
-Ryan[/QUOTE]
Is there a system sound associated with clicking on your icons by default?  I found that on my fresh install I had to remove the sound as it interfered with sound playing in many games when launched from the menu...if this is the case, you can turn such sounds off under (System/Preferences/Sound), going to sound events tab, and check under 'User interface events' and 'System events'.  Hope this fixes it for you!

---

### Post by klahjn on 2006-04-04
wierd that something like that would interfere with the sound for the entirety of the program being ran.  It does sound logical if there is an error with the sound being played, but if that is the case, wouldn't that be a problem to report to wine devs?

---

