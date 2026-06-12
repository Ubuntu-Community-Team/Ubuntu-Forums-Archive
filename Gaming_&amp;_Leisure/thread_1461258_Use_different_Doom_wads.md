---
title: "Use different Doom wads?"
date: 2010-04-24
forum: Gaming &amp; Leisure
---

### Post by stevek123 on 2010-04-24
I have a fresh install of karmic. I downloaded & installed Freedoom from the software ctr. I downloaded & installed prboom from Debian (fixed a bug the repo version had). Freedoom runs fine. I have a stack of sweet one or 2 level wads that run on doom2 engine - I got these to play on my mp3 player using Rockbox. I'd like to try & play them on the comp but do not know where to install them. In Rockbox, I made a folder called 'addons' and stuck'em in there. They run great. 
I found /usr/share/games/freedoom/doom2.wad ...but other folders link to this too... not sure what to do...

---

### Post by DoktorSeven on 2010-04-24
With prboom you need to use the commandline to specify pwads, which is likely what you mean -- these are WADs that are "patch WADS" that are meant to be used with an existing game WAD like the original Doom 2 WAD or FreeDOOM:

prboom -iwad /path/to/doom2.wad -file /path/to/yourpwad.wad

e.g.

```
prboom -iwad /share/Games/Doom/iwads/doom2.wad -file /share/Games/Doom/pwads/hr2final.wad
```

Those are the locations I have WADs (the base game files) and my PWADs (the extra level addons like you are talking about, that run on top of the original DOOM WAD), and I'm running the "hr2final" PWAD on top of the original Doom 2.

Note that many PWADs are made for the original Doom 2 WAD and might not work as expected using FreeDOOM.

---

### Post by stevek123 on 2010-04-27
Thanks for reply!
Command line.... ok
Sorry if i seem a little dense ... so I need to make a file = /share/Games/Doom/pwads/    and stick my pwads (yes I am sure most are pwads) in there... then use command line to specify which one to play... all that seems straight forward... but I dont know how to start the game from there. 
Does this begin the game? or do I then start it from my normal gui (x) ? or do I need to start it from command line also?
If this sets it up to run the pwad in the config file or somewhere, what do I need to do the get it back to 'default'?
Also, I noted that my base wad (doom2.wad) file is in /usr/share/games/freedoom
and that /usr/share/games/doom is the path to the prboom wad and a link to the doom2 wad. 
Which is the appropriate path to include the pwads?

---

### Post by weegee101 on 2010-04-27
Have you thought about trying the Doomsday Engine rather than prboom?  It comes with a very nice python-based GUI for configuring the game.

[http://dengine.net/](http://dengine.net/)

---

### Post by stevek123 on 2010-04-28
thanks but I've got it figured out now. The commandline using prboom -file /path... worked great with the 2 pwads I've tried. I havent tried to save a game yet for those with multiple levels... but I'm OK! the -file option was in the readme file - I just didnt know what to do with it.

---

