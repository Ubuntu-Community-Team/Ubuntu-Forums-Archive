---
title: "Every thing running slowly..."
date: 2009-04-25
forum: General Help
---

### Post by BlackRat90 on 2009-04-25
yesterday i downloaded and installed ubuntu 9.04 
i installed onto my laptop and ever sense then **EVERYTHING** on my laptop seems to run slower.
my internet seems to run slower (i normally plug my xbox into the wireless connection so i can use my wifi with it without buying an adapter, its been saying the connection is slower now), 
firefox runs way slower **(lots** of lag with it), 
one of my favorite games (Eternal Lands) runs way slower at only 8-10 fps normally 25-30. 
my mouse is seeming to have weird problems (like randomly clicking when im not clicking, it might be a hareware problem)
Also Skype can no lower connect my calls...i really need this to work
 but im sick of everything running way to slow...with XP it all ran perfectly fine.

i got a thinkpad T41
ATI radeon mobile 9000
and 512mb of ram.

if anyone knows a way to update something like some drivers that i cant seem to do, it would be very appericted, otherwise i might have to go and reformat back...

---

### Post by BlackRat90 on 2009-04-26
I I ran the glxgears test and it came up at about 800 fps, i read that this could mean my graphics drivers arnt right? is there a way to fix this?

---

### Post by blakkandekka on 2009-04-27
This may be unrelated but my T41 with a 7500 was very stuttery (especially Compiz perfotmance) after an upgrade to Jaunty until I added the following line to the device section of /etc/X11/xorg.conf.

Option "AccelMethod" "XAA"

It just makes explicit the hardware accelleration method used.

---

### Post by TimMann on 2009-06-12
I had the same problem on my T41 with Radeon RV250 [Mobility FireGL 9000], and setting that option to XAA fixed it for me too. I guessed this independently and then found the forum posts here about it only afterward.

"man radeon" says that the default is now EXA, not XAA, so setting the option to XAA definitely changes it.

Googling a bit, it looks like EXA is a relatively new thing and may still need some performance tweaking.  See [http://cworth.org/tag/exa/](http://cworth.org/tag/exa/).

---

