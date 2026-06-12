---
title: "Openal-alsa"
date: 2006-04-07
forum: Gaming &amp; Leisure
---

### Post by darkbrain on 2006-04-07
Hi guys,
    [Openal-alsa]("http://dino.e4a.it/openal-alsa"). This is an implementation of OpenAL library using ALSA as the only back end. OpenAL - Alsa is only a modification of the original library OpenAL-alsa-emu10k1 made by C.J.Purnell. I've simply replaced all code relative to emu10k1 processor, with a more compatible one, so now it's should work with every sound card that supports multiple sub streams.

try it!
   Dino

---

### Post by minisori on 2006-04-07
Hey good to know you solved that issue i told you. I will check it when i get home.

Thx and good work :)

(I'm Antonio :P)

---

### Post by Zeroedout on 2006-04-07
[quote=darkbrain]Hi guys,
    [Openal-alsa]("http://dino.e4a.it/openal-alsa"). This is an implementation of OpenAL library using ALSA as the only back end. OpenAL - Alsa is only a modification of the original library OpenAL-alsa-emu10k1 made by C.J.Purnell. I've simply replaced all code relative to emu10k1 processor, with a more compatible one, so now it's should work with every sound card that supports multiple sub streams.

try it!
   Dino[/quote]

wicked sick!!! But what are the advantages to using this, as say the version of openal that comes with UT2004?

---

### Post by minisori on 2006-04-08
They are hardware accelerated.

---

### Post by Yagisan on 2006-04-08
Will you send that upstream to the openal people ?

---

### Post by darkbrain on 2006-04-08
[QUOTE=Yagisan]Will you send that upstream to the openal people ?[/QUOTE]
Do you mean to submit this project to openal mainstream([www.openal.org)?](www.openal.org)?) 
Well this is a totally new implementation witch a bit of code is taken from mainline, anyway it's not compatibile. I've posted this work at the mailling list of openal but i didn't saw any intereset on it :( so for now i'd like to spread it a bit. If a good group of people use it the guys at openal.org will take intereset in this version, if so will see. Anyway audio drivers for linux are terrible! No documtation for alsa guys about the hardware so we can't use all nice features of ours soudcard, it's sad.

bye,
   DarkBrain

---

### Post by minisori on 2006-04-08
Yes im still wondering if there would be ever support for 6.1 :???:

And i use your version :D

---

### Post by minisori on 2006-04-11
Oki tested and working very good. The possitional audio seem to work better on games and play by the right speakers.

The only thing left probably its more playback chanels.

(Tested with tremulous and ut2004 at moment)

---

### Post by jfx on 2006-04-12
Sorry, don't wan't to ask some stupid queations.. but can you give a quick howto for installing it?

---

### Post by minisori on 2006-04-12
[QUOTE=jfx]Sorry, don't wan't to ask some stupid queations.. but can you give a quick howto for installing it?[/QUOTE]

To use with ut2004 for exmaple just overwrite the file openal.so (i think was that the name there?) in ut2004/system folder whit libopenal.so.0.1.5 wich you just compiled. (remember to do a copy of openal.so first).

NOTE: The following is for dapper so check before what is the symlink for libopenal.so.0 to restore after.

If you want to use with tremulus for example or any game based on icculus? quake 3, you can symlink /usr/lib/libopenal.so.0 to the one you just compiled. 

```
sudo ln -fs libopenal.so.0.1.5 /usr/lib/libopenal.so.0
```

I dont kknow if there is another way just copying the liopenal.so.0.1.5 inside their folders. Remeber to restore after the symbolic link wich is  libopenal.so.0.0.8. 

```
sudo ln -fs /usr/lib/liopenal.so.0.0.8 /usr/lib/libopenal.so.0
```

You can copy too if its needed any of the setups for the speakers inside etc to ~/.openal-speakers.

For doom 3, hmm dunno look in the console what library load at the begining :P

The only bad thing is that only support 21 sources at most at the moment and may result sometimes in the feeling that you are loosing some sounds.

---

### Post by jfx on 2006-04-12
Great thnx ! :-D

---

### Post by darkbrain on 2006-04-13
[QUOTE=minisori]
The only bad thing is that only support 21 sources at most at the moment and may result sometimes in the feeling that you are loosing some sounds.[/QUOTE]
It's true that you loose sounds if n° of voices allocated by games are more than yours driver can handle. (Kill atrsd,esd or similar to free at least one voice). To not loose any sound, for games like ut2004 or america's army, go to the relative .ini file and set the maximus n° of voices (more info into README).
Anyway 21 sources is a problem caused only by the driver of emu10k1 chip. Take a look to this thread for more explanations:
[http://www.mail-archive.com/alsa-devel@lists.sourceforge.net/index.html#12913](http://www.mail-archive.com/alsa-devel@lists.sourceforge.net/index.html#12913)

If i understand to have more voices you need to fork the driver and change the use of internal timer.

bye,
   DarkBrain

---

