---
title: "Emulation woes :("
date: 2009-02-20
forum: Gaming &amp; Leisure
---

### Post by ambidextrousone on 2009-02-20
hey guys, basically, im looking for a good mame emulator, reasonably up to date, with a focus on my usb joypad working.

i took kxmame from the repo's - but although it seems to run the games, joypad compatibility is non existant, theres settings here to allow it, but it makes no difference - making the adjustments to my controls within mame itself, the joypad just cant seem to work

help :P

---

### Post by BoyOfDestiny on 2009-02-20
Try [sdlmame]("http://rbelmont.mameworld.info/?page_id=163")

It is kept up to date with the current mame, has a built in launcher and in-game menu (if you press tab) to configure whatever you like. If your joystick is supported by Ubuntu, it will work with this. It should be out of the box in fact.

If you need a proper graphical front-end, try [gelide]("http://gelide.sourceforge.net/index.php?sect=home&lang=en").

---

### Post by binbash on 2009-02-21
Gelide is a nice frontend, there is also wahcade : [http://www.anti-particle.com/wahcade.shtml](http://www.anti-particle.com/wahcade.shtml)

---

### Post by disturbedite on 2009-02-21
there is also mamepgui:
[http://www.mameworld.info/ubbthreads/showthreaded.php?Cat=&Board=news&Number=180321&Forum=All_Forums&Words=mamepgui&Match=Entire%20Phrase&Searchpage=0&Limit=25&Old=allposts&Main=180321&Search=true#Post180321](http://www.mameworld.info/ubbthreads/showthreaded.php?Cat=&Board=news&Number=180321&Forum=All_Forums&Words=mamepgui&Match=Entire%20Phrase&Searchpage=0&Limit=25&Old=allposts&Main=180321&Search=true#Post180321)

it supports multiple mames, but sdlmame is best for linux.

---

### Post by PhoenixDream on 2009-02-27
Im having trouble getting the ROMS to work with sdlmame, I have the frontend installed and working fine, I just cant seem to add the ROMS correctly. They are the same ROMS I have used with MAME32 on XP and they are all zipped etc.

---

### Post by BigSilly on 2009-02-27
What a lot of people don't realise is that SDLMAME is released at roughly the same regular rate as normal MAME. This means that it's highly likely your ROMS are outdated, and won't be compatible with the latest version. If you have a collection of 0.106 ROMS, then you should be fine with K/GXMAME. Anything after that and you'll need to know what set you have, and which version of MAME to track down. This can prove tricky indeed. MAME, it has to be said, is a real pain in the proverbial, whichever OS platform you prefer.

I kept a .deb of SDLMAME 0.120 which was built for Gutsy, and have a full set of 0.120 ROMS that are fully compatible and working. The latest version 0.129 I believe, and if you want to use that, you'll need a compatible 0.129 set. I might upgrade to 0.130 soon though. But you get the picture. That's how MAME (and SDLMAME) works.

---

### Post by hikaricore on 2009-02-27
Roms don't really get outdated....

The various data files that MAME uses however might.
You sure this isn't what you're talking about?

---

### Post by BigSilly on 2009-02-27
I don't know the technicalities of it, so please feel free to illuminate me. All I do know is that a great number of older ROMS will not work on subsequent versions of SDLMAME, and that there can be many reasons for this. The only way to be sure, is to match your ROMS against the version of MAME you're using.

---

### Post by hikaricore on 2009-02-27
I've had the same public domain ROMs for the last several years and they've always worked with every version of MAME I've used them with.

The issue like i said is the DAT files and regressions in the MAME code itself.

---

### Post by wingnux on 2009-02-27
Have you edited your mame.ini with your rom path?

---

### Post by BoyOfDestiny on 2009-02-28
Some ROMs do indeed change.

> As time passes, MAME is perfecting the emulation of older games, even when the results aren't immediately obvious to the user. Often times the better emulation requires more data from the original game to operate. Sometimes the data was overlooked, sometimes it simply wasn't feasible to get at it (for instance, chip "decapping" is a technique that only became affordable very recently for people not working in high-end laboratories). In other cases it's much simpler: more sets of a game were dumped and it was decided to change which sets were which version. 

[http://mamedev.org/devwiki/index.php/FAQ:ROMs#I_had_ROMs_that_worked_with_an_old_version_of_MAME_and_now_they_don.27t.__What_happened.3F](http://mamedev.org/devwiki/index.php/FAQ:ROMs#I_had_ROMs_that_worked_with_an_old_version_of_MAME_and_now_they_don.27t.__What_happened.3F)

If you can recommend other free roms (besides the ones mame dev has, I'd love to give them a go)

Anyway, those having problems, check your mame.cfg or sdlmame.cfg file. 
It's likely not pointing to your roms folder 
Should be, for example: 
/home/you/mame/roms

If you have roms or chds in multiple folders, 
append a ; in your cfg file an put the additional locations.

---

