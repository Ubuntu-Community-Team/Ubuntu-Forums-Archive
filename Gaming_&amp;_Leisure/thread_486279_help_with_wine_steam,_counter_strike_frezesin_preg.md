---
title: "help with wine steam, counter strike frezesin pregame menu"
date: 2007-06-27
forum: Gaming &amp; Leisure
---

### Post by jacob01 on 2007-06-27
i have just installed steam using wine and logged into my existing account and after downloading counter strike source and running it goes into the pregame menu were it say loading in the bottom right side of the page and freezes
i have been trying to get this working for a couple of week and just got steam installed with wine it loads steam fine and shows everything normally but when i go to launch the game it show the background of the menu but doesn't show any thing else, i have installed the fonts and like i said steam runs normally and i have looked for other posts of similar things but nothing has worked

im not sure if the video card would cause this problem or what is wrong but every time i do this i have to do a hard shutdown by holding the power button for 8 seconds

i have a dell e520 that came with ubuntu 7.04 loaded on it has worked great with no other problems
im using wine 0.9.39

it has a core 2 duo
one gig of ram
250 gig hdd
i think intel grafics accelerator

please help

---

### Post by dfreer on 2007-06-28
hmmm. did CS:S work in windows for you? cuz maybe I'm wrong, but i don't think that onboard intel video card would be able to run CS:S in any OS. Does original CS work, or any other steam game you have (that isn't built on source)?

---

### Post by jacob01 on 2007-06-28
yea im sure the picture wont be good but i figured that it would at least load the pregame menu and try to play the game but instead it frezes and i have to restart my computer

i have read other posts were the sound drivers may cause this but im not sure

---

### Post by justin whitaker on 2007-06-28
Four things which throw a CS:S install out of wack on Linux: Video Drivers, Sound Drivers, Missing Font, Mozcontroller. Start with those. Not sure that you can really get it up and running on Intel graphics, but you might try using DX7 or 8 to elimnate some of the high end graphics.

---

### Post by jacob01 on 2007-06-28
i have the latest drivers installed for the graphic in Ubuntu but do the windows drivers have to be installed in wine also.

i have installed the fonts already so i don't think its that

---

### Post by jacob01 on 2007-06-28
i ran astro pop like and when it launched it showed the window but  inside it was all white so that didn't work eithor

any ideas

i made sure oss sound driver was selected in winecfg but i still work. don't know on the video drivers if they have to be installed in wine or what to do

---

### Post by dfreer on 2007-06-29
no, you don't install any drivers in wine, just make sure they work correctly in ubuntu. I'm thinking the tahoma.ttf is only needed for steam, which works for the OP so it must be installed correctly. mozcontrol (which shouldn't be needed in the newest version of wine) would only affect the steam store and MOTD on certain servers. Sound may cause a problem, but if it is working correctly in ubuntu the only thing to do in wine is try messing with the sound settings (OSS is generally recommended for steam games, I'd stick with it).

try doing a <Ctrl><Alt><Backspace> instead of a hard reboot, in case you haven't already.

As for video, do you know if direct rendering is enabled?
```
glxinfo | grep rendering
```

---

### Post by jacob01 on 2007-06-29
no i tried ctrl+alt+backspace it doesnt respond to anything

---

