---
title: "Just looking for a good sim type to play on an older computer"
date: 2015-03-05
forum: Gaming &amp; Leisure
---

### Post by Ben_Cook on 2015-03-05
Just wondering if anyone knows of a good sim game I can play on my old machine.  Here are my basic specs - 2.33 Ghz intel core 2 duo processor (E6550), 2 GB RAM.  For what it's worth, it has an 82Q35 express integrated graphics controller.  I have no idea what that means, just thought I'd put it out there.  I tried to play a demo of GTR 2 through playonlinux, but it just tells me wine crashes.  I own the Sims 2, but it gives me a directX9.0c error when I try to play it....it's not available through playonlinux.  I'm just looking for some sort of game I can play, but I don't really know what I'm doing.  GTR 2 is one I'd really love to play, but I don't want to buy the full version if it simply isn't going to work. Oh, I'm running Xubuntu 14.04.  Thanks for any help/suggestions!

---

### Post by mastablasta on 2015-03-06
your graphics chip is the biggest issue. what kind of sims are you looking for? sims2 have garbage rating on wine. there are many types of simulation games available. many will need stronger graphics chip (maybe dedicated GPU card).

GTR 2 has good rating in wine. perhaps you are missing some libraries or something?

how about something like need for speed underground 2 it's pretty descent game and doesn't seem so demanding. or maybe some other games form NFS franchise they usually have gold rating.


otherwise if you are a bit into strategy sims try Open TTD. it can be quite fun and is not graphically demanding. there are also a few other sims like that. but can't remember them from the top of my head. old DOS games can also run well on these underpowered graphics chips. for example Pizza Tycoon, Rollercoaster tycoon, sim city...

---

### Post by Ben_Cook on 2015-03-06
Thank you...I might give open TTD a try.  When I try to play GTR 2 it just says "Error in POL_Wine Wine seems to have crashed".  I like racing sims, and it seems my computer should be able to run GTR.  But unfortunately I don't know ubuntu/linux very well, so I don't know what the next step would be to see if I can fix it

---

### Post by mastablasta on 2015-03-09
try to run it from terminal. type wine and then path to the file that starts GTR (you can drag and drop the file into terminal)

so for example:

wine gtr.exe
wine /home/ben/.wine/c_drive/program files/gtr.exe (or whereever the file is)

the terminal Will give you any error output that Will stay after wine crashes. then you can see where the error is.

a comon mistake is when users have 64 bit OS and they do not create 32 bit wineprefix for 32 bit games/applications. by default on 64bit os 64 bit wineprefix is created.

---

