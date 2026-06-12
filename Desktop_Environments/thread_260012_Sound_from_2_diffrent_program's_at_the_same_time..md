---
title: "Sound from 2 diffrent program's at the same time."
date: 2006-09-18
forum: Desktop Environments
---

### Post by joneZ on 2006-09-18
Hi,

I have bought a new laptop ( Dell D420 ) and now I have little problem 
with the sound , I can't get music from 2 diffrent programms. 

For example, i have to close rhythmbox for example, even if it is not playing, when I want to here something when I'm at youtube.com or watch a DVD.

It does not matter if's mplayer or totem ( gstreamer ).

I think I don't have the problem on my old one ( Dell D600 ).

It looks like like that the program's that opens the alsa device is blocking it.

Is there a solution for this ... It is really frustrating if you have 2 close rhythmbox every time you want watch a little flash-clip or something
else.


Using 
- Dapper up2date
- Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)


Maybe someone know something .... O:) 
Greetings
Erik

---

### Post by Haegin on 2006-09-18
Linux has several sound programs to manage the playback of sound. The main ones I know are ALSA, arts, esd and osd. I think you need one of them (preferably alsa as I know that works) to play back multiple sounds. I would recommend checking what you are using and if its not working then try installing alsa.
KDE uses arts as the sound daemon so if you are running kubuntu or use kde you probably need arts.

---

### Post by someguyouknow on 2006-09-18
I achieve this by starting Opera using "aoss opera"...
this way, i can listen to music and youtube.com if i choose...
i assume the same can be done using firefox...
there is also another way to do it for firefox by editing a file...
if you prefer that way, let me know...

---

### Post by joneZ on 2006-09-18
Thx all,

I found out that I had 2 Sound Systems installed esd and alsa. Dunno why, it was a fresh install. Maybe some a stupid dependency from a package .

I removed esd. 

And it works like charme. Maybe firefox searches for esd first, if found
it can't play because alsa is installed. Maybe that is the reason.

Bye
Erik

---

