---
title: "SDLMame, gngeo rom help"
date: 2007-11-16
forum: Gaming &amp; Leisure
---

### Post by aashay on 2007-11-16
afaik, mame is capable of emulating neo geo roms. But so far, every neogeo rom i've put in the /usr/locas/share/games/sdlmame/roms folder has been ignored by it. Is there a bios image or anything i should get in order to make it work? 
An alternative I tried was gngeo. But it keeps on blabbering about "not valid romsets" or something. Ive put in the bios for gngeo in the correct location. Is there something i'm missing here?

---

### Post by disturbedite on 2007-11-16
read this:
[URL="http://www.dweasel.com/agmfaq/index.html#toc4.4"]http://www.dweasel.com/agmfaq/index-4.html#ss4.4
[/URL]

---

### Post by aashay on 2007-11-16
> **disturbedite said:**
> read this:
[URL="http://www.dweasel.com/agmfaq/index.html#toc4.4"]http://www.dweasel.com/agmfaq/index-4.html#ss4.4
[/URL]Does that mean I downloaded the *wrong* type of rom?

---

### Post by disturbedite on 2007-11-16
not exactly, no.
i'll try to explain this to the best of my ability.
mame uses a parent/child relationship for storing roms.  (this might be best illustrated by an example later).

you can store roms/archives two different ways, "Split" or "Merged".  what split does is it keeps child roms in separate archives from their parents.  merged does just what it sounds like, it keeps the child roms in the same archive as the parent rom.  the name of the merged archive will be the parent rom's name, with all the child roms inside the archive as well).

for instance, lets take Marvel vs. Capcom or X-Men vs. Street Fighter.  the latest hardware revision date of the U.S. version of the game is the "parent" of the all the variations of the game.  (iirc correctly in this example, the U.S. version is the parent, but even if i'm not correct you should be able to get what i mean).
so, if you have the romset merged, in this example, the latest U.S. version of mvc's or xvsf's archive will be named something like:  mvscu.zip or xmvsfu.zip and each of those archives will have every variation of the game (like japan, eur, or a different revision) in it.
if you have the romset split, (which is recommended even tho it might seems less efficient), then there will be a separate archive for each version of the game, like mvsca.zip, mvscb.zip, etc.

hope that is understandable.

so you may be missing more roms.  (oh, and i almost forgot, i believe neogeo games do require a bios or multiple bios, let alone that you may be missing more roms).

(anybody feel free to correct anything i said, just in case).

---

### Post by nartooki on 2007-11-16
are you sure you have all the neogeo bios files? a google search of mame bios takes you to a place with a bunch. what games are you trying to get to work?

---

### Post by BigSilly on 2007-11-17
Yup, you have to be sure you have all the Neo Geo BIOS files, then you should be fine. They're easily available around the net.

---

### Post by hikaricore on 2007-11-17
I'm sorry folks.  I can't allow continued talk of roms and rom bios files to continue here.
I don't want this to make me the bad guy, but there are other methods/sites for these discussions.  Not to mention IM clients, IRC, and similar services.  ^_^

Thanks for understanding.

--Aaron

(additional posts about this matter will be jailed and you will be warned)

---

