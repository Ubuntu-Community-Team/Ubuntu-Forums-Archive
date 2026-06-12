---
title: "Ubuntu 9.0.4 detects the wrong monitor and im stuck at 800x600"
date: 2009-05-17
forum: General Help
---

### Post by ShinigamiKiba on 2009-05-17
At the moment this is the the only computer and monitor i have, my other computers and monitors are in another house so i'm stuck with this.

I have a Relysis 17" and Ubuntu used to detect it just fine until one day when all on its own it decided I have a 15" Relysis, made 800x600 the highest possible resolution at any refresh (only 75 and 85Hz are avaliable atm) and that was it.

I don't know what graphics card i have, I got this computer for free from my aunt cause she won it and didn't need it and I installed Ubuntu to it, it's a fine system for an Ubuntu machine, but other than that meh, and it's just some integrated graphics card but it can do Compiz so that's cool.

Again, all was well, one day it just happened.
I'm not very computer literate, so whatever you do, please keep your explanations simple and easy to understand, but keep in mind, while I do say I'm not very computer literate I'm not a complete and total noob so I know, for a fact i didn't do anything to make it do this.

---

### Post by ShinigamiKiba on 2009-05-17
This wouldn't have been that much of a problem if I could at least set up compiz at 800x600, but the compiz manager thingy requres at least 1024x768 to work properly, it's a mess on 800x600 and you can't even click half the stuff cause it moves around and crap.

---

### Post by ShinigamiKiba on 2009-05-17
Sorry for triple posting everyone, but I just remember something that might be important 

The day this happened, after booting the computer up it was set to some high resolution AND at a low refresh rate, i lowered it down to 800x600 and that's when I got stuck at 800x600 for good.

Before all this i didnt have this crazy *** problem, i can't even begin to understand how to fix this, please if i have to use the terminal be very clear about it cause i don't understand that stuff well

edit: I tried restarting and keeping the monitor off, i even turned the computer off and let it boot to ubuntu with the monitor off thinking it would clear whatever happened, but nothing.

---

### Post by ShinigamiKiba on 2009-05-17
Please someone help me.
I'm stuck at 60Hz now, I can't use the computer like this, I've been trying to get it back to at least 75 or 85 for the past half hour and my eyes hurt like never before.

I have SEVERELY damaged eyes and low refresh rates make my eyes hurt real bad lol

I unplugged the monitor, restarted and let ubuntu load up that way, then i went into low graphics mode, set it to default configuration and all that, eventually got a choice of more resolutions, did what i had to do in Compiz and now I'm stuck at 60Hz and an Unkown monitor.

I need to get off the 60Hz and I need to get off it now, I'm typing this with my eyes closed lol my eyes can't take much more of this.

please someone help me at least get back to the fake relsys 15" drivers or whatever anything just not this 60Hz stuff

---

### Post by yim on 2009-05-17
you might try sudo dpkg-reconfigure -phigh xserver-xorg in terminal and then logout and see if login you have options to get your resolution back

ps when and if you get the wizard to show up don't hit the test button it usually fails for me but will actually work.

hope that helps

yim

---

### Post by ShinigamiKiba on 2009-05-17
thanks man think that helped. 
finally got off 60Hz and back to 85Hz
still detects it as a 15" Relysys, now i have a few more resolution options but it don't matter, i was at least able to back to my studying after i fixed it :D

I have no idea what i did btw, but hey, works for now

---

