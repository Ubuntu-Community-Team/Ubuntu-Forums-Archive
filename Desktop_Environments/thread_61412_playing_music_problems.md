---
title: "playing music problems"
date: 2005-08-31
forum: Desktop Environments
---

### Post by tonysathre on 2005-08-31
i formatted a FAT32 partition so i can share my music back and forth between linux and xp, some songs are ripped to the FAT32 with windows media player and some are downloaded as mp3's, in ubuntu i tried using every media player i have including mplayer, xmms, noatun among others and none of them will play the songs that i ripped from cd but will play cd itself, only the mp3's that i downloaded will play.  anyone know what could be causing this and how i can fix it

also, i have installed w32codecs so thats not the issue

---

### Post by Lord Illidan on 2005-08-31
Am I right in assuming that the songs you ripped using Media Player are .wma?

If so, maybe you have a wierd type of DRM protection management enabled on Media Player which prevents you from hearing them with unsupported software..

Can you try enabling all their permissions?
Also, regarding mplayer, did you install the w32codecs as according to the Ubuntu Guide?

Third.. maybe vlc can help out..

EDIT : If none of this helps, you might have better luck in converting to the .ogg file format. I am sure that there are utilities in XP to do this...

---

### Post by tonysathre on 2005-08-31
the files are cda, and some are wma but i dont remember if those worked or not, but i know for sure that the cda's dont work

i installed w32codecs via synaptic

---

### Post by gnutux on 2005-09-01
You must rip it in MP3 or OGG for Linux to read it properly, DO NOT use WMA.

gnutux

---

### Post by f1dave on 2005-09-01
Well wmv works, why not wma? :S

---

### Post by tonysathre on 2005-09-01
k ill try that

---

### Post by Pitou on 2005-09-01
I know that it depends with which media player you encoded you wma.

I think that with wmp9 or below you wma will play but not with wmp10.

I have some wma that works and some that don't.

Pitou!

---

### Post by Elv13 on 2005-09-01
apt-get remove xmms
apt-get install xmms

the layer 3 block  will dispear (supose to, if not, but crossover and install itunes)

---

