---
title: "Installing Spring"
date: 2010-07-30
forum: Gaming &amp; Leisure
---

### Post by Audiosurfer on 2010-07-30
I'm having trouble installing Spring RTS. How do I do this?

---

### Post by Cresho on 2010-07-30
I was blown away by the install method as well.  I quite didn't understand the lingo.

---

### Post by huwjenjinn on 2010-09-13
> **techjunkie7554 said:**
> I'm having trouble installing Spring RTS. How do I do this?

I'm not sure where you're getting stuck but if you're running Lucid then I hope this will help you out.

You need to link to the Spring launchpad repository to get the latest updates, else you won't be able to play, by adding ```
**ppa:spring/ppa**
``` to your software sources. Then install SpringLobby and SpringEngine through Synaptic package manager. (I'll try and come back and add the code for you when I get back to my machine at home).

Once you have these installed you should be able to fire up SpringLobby from within the Games application area. Simply register a login name with Spring and connect away. Once connected you should then be presented with a list of active games currently running. This is your starting point for anything to do with the SpringEngine, even running a single player match.

The Engine isn't a game in it's own right so you'll need to download that too, but doing it from within SpringLobby was easiest for me. Simply right clicking on the Mod (game) you wish to play and select it to download. Example:

So, if you want to play Balanced Annihilation for example, and who wouldn't, find the latest version (think it's BA 7.18 at the time of posting and the Lobby is 0.92) right click on the row/host running this version and choose download from the pop-up menu. This will automatically install that version of the Mod, you can watch in the Download tab, and once installed allow you to both join, host and run that Mod single player.

But before you can do any of the above you'll also need to download a map. Do the same for Maps as you did with the Mod to start with, although you can download these directly and copy them into your ```
.spring/maps/
``` folder inside your home directory. Maps can be downloaded from the [www.springfiles.com](www.springfiles.com) site. Some people I play with have difficulty downloading Maps from within the SpringLobby area so get them from there first, personally I've not had  a problem either way.

Just for your reference here's a link to the PPA for Spring RTS under Ubuntu

[https://launchpad.net/~spring/+archive/ppa]("https://launchpad.net/%7Espring/+archive/ppa")

---

### Post by lars.modig on 2010-12-24
Hi,

Actually I would like to test the StarWars game under Spring. But I have a hard time to find it and then understand how to start it...

So then I just tried to use the software central for ubuntu and downloaded "Panic Kernel".

But when I start that I get "Segmentation fault (SIGSEGV)". When looking at the Terminal text it says (quite clear) that I have a terrible video card (i915). so the game may crash... And yes it does. 

Is it any idea that I still try to get ImperialWinter to run or should I just give up?

In case you think I should try some tricks how should I 

1. Just get "Panic Kernel" run without crashing?
2. Import ImperialWinter with maps and everything so I can run it
3. Find the latest Beta for ImperialWinter.


Thank you

Lars

---

