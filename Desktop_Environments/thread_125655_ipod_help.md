---
title: "ipod help"
date: 2006-02-04
forum: Desktop Environments
---

### Post by guine on 2006-02-04
I have been using gtkpod to get songs on my ipod but most of my music is saved as oggs and I was wondering if there was any program that could convert oggs to mp3s while transfering music to the ipod or if there was a simple way to convert all of my oggs to mp3s at once.
Also, my ipod always has do not disconnect displayed when it is connected to my computer.  Ive just been disconnecting it anyways because I couldnt figure out how to do anything about this and I was just wondering if I was doing something wrong or if my ipod will always do this and I should just continue to disconnect it while it still says do not disconnect.
Thanks

---

### Post by Patrick-Ruff on 2006-02-04
when it says do not disconnect, it really only refers to while transfering data. if yuo have it plugged in and it isant doing anything, (like not playing music or no data transfer etc) then it wont hurt it (I do it all the time lol).  also, why would you want to transfer it to MP3 anyways?  you cant copy music back off of it.

---

### Post by kperkins on 2006-02-04
[QUOTE=Patrick-Ruff]... also, why would you want to transfer it to MP3 anyways?  you cant copy music back off of it.[/QUOTE]
**Because ipods don't play ogg vorbis files**, and he wants to transfer his music to his ipod.  
There's a program called normalize-audio, in synaptic, that'll convert oggs to mp3s (of course you'll lose quality, because you're going from one compressed format to another--if you have the original cds you may want to re-rip the music to mp3s)  
Install normalize-audio, (and the recommended vorbis-tools and mp321)
open a terminal cd to the folder with your oggs (if you want to keep the oggs copy them first, and run this on the copies, because this converts them, and doesn't make a copy)
Then in the folder with the oggs run this command:
```

normalize-ogg --mp3 *.ogg

```
That'll convert every ogg to an mp3 (and normalized the volume). May take a while if you have a lot of them. (you can also adjust the bitrate if you want--read the normalize-ogg man for that)
That's the easiest way to convert a bunch of ogg files to mp3s, the only problem is that it doesn't save the id3 tags.  There's a perl script that converts oggs to mp3 (called ogg2mp3) here: [http://marginalhacks.com/bin/ogg2mp3](http://marginalhacks.com/bin/ogg2mp3) that does save the id3 tags--you'd have to set it up yourself, as I'm not familiar with it.
Or, you could take the ipod back, and get a player that plays ogg files (i recommend the Cowon Iaudio series)

---

