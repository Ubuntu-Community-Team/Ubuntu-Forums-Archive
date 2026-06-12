---
title: "Cedega freezing issue"
date: 2005-08-03
forum: Gaming &amp; Leisure
---

### Post by Sirrob01 on 2005-08-03
just on the off chance someone else has had this problem (also posted it to cedega forums)

Ub 5.04
Ced & Pt2Ply latest versions

all pt2play test are green

pt2play loads into its GUI fine and I can hit install button enter path to setup all okay but as soon as I hit continue pt2play stops responding (instantly I cant even get any error output) tried starcraft & empire earth same result, tried two different cd-rom drives incase the first was faulty

the only error I had during installation was this

488 warning In AGP Aperture size Test: AGP Memory available: NA(NV_vertex_array_range extension not present)

from a bit of reading i did this would cause more in game performance issues, but thas only a guess, feel free to fill me in and how to fix it :).

running an old athlon 1600xp 768mb ram radeon 9600xt

anyone run across this before?
thanks for any help

---

### Post by Mishura on 2005-08-04
Not an expert, but:

NV_vertex_array_range

looks like a NVIDIA extension, that isn't present with ATi.  Clue me in if I'm wrong here.

---

### Post by Sirrob01 on 2005-08-04
small update, when i force close I get this message in terminal

/usr/bin/Point2Play: line 45: 9236 Killed ${P2PPATH}/bin/python${P2PPATH}/Point2Play_gui.py "$@" 

seems to be a python/code problem, but Ive tried re-installing python with no effect.

S01

---

### Post by Kemotaha on 2005-08-04
I have noticed that sometimes it takes a couple minutes before a game or installer comes up.  but usually P2P doesn't stop responding so I don't know.  Have you posted this in the Transgaming forum?  I don't think it is the system.  I had it running on my Athlon XP 2000+ before I upgraded.  It only had a ATI7500 AIW card.  

Sorry I can't be of more help

---

### Post by Sirrob01 on 2005-08-04
yep posted to the transgame forum...thought someone else might have come across the problem before, but seems it maybe unique to my system/setup.....i love computers :---)

---

### Post by Sirrob01 on 2005-08-07
just for anyone else who may in counter this.

I had a previous version of wine installed which seems was messing up the cedega install process.

removed it and then started from scratch with point2play all runs fine

to push the P2P installer through from scratch insure the file under home/<username>/point2playrc is deleted, I had to remove it manually even after a supposed full un-install.

thanks for the help/reading

S01

---

