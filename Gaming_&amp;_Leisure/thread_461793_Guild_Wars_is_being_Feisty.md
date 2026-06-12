---
title: "Guild Wars is being Feisty"
date: 2007-06-02
forum: Gaming &amp; Leisure
---

### Post by Dev0205 on 2007-06-02
Linux friends,

I've been able to get WoW, Warcraft III, and Starcraft working under wine but I keep running into a brick wall with Guild Wars. I have a Nvidia FX5600 and am using the command ```
env WINEPREFIX="/home/devin/.wine" wine "C:\Guildwars\Guild Wars\Gw.exe" -dx8 -noshaders -windowed >/dev/null 2>&1
``` to launch GW "As suggest from a guide". However, the game gets to where the loading screen would come up, but there is no video shown in the Window. You just seen a grey frame around the current desktop, does that make sense? Any of you have an idea what is up? I've tried setting Wine as an emulated Desktop and also running the game with out the -Windowed mode. I'm stumped. 

Dev

P.S - I have no desire to try Cedega "Monthly Fee's are the Devil"

---

### Post by hikaricore on 2007-06-02
I may be mistaken, but my understanding of WINEPREFIX is that it is used to set the base directory
from where the application will run.  It's possible that the game can't find it's data files, try:

> WINEPREFIX="/home/devin/.wine/drive_c/Guildwars/Guild Wars"

I have no experience with GW, just with wine in general, and that's my best guess without searching around (i'm tired >.< sorry)

Good luck,

--Aaron

p.s. Also the wine application database might have some more useful tips for you: [http://appdb.winehq.org/appview.php?iVersionId=7530](http://appdb.winehq.org/appview.php?iVersionId=7530)

---

