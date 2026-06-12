---
title: "Bad Performance from Totem"
date: 2005-03-25
forum: Desktop Environments
---

### Post by Corey on 2005-03-25
I'm getting really bad performance from totem when playing videos. Sometimes it plays fine but the audio is hald a second behind. Other times The audio will play at a constant speed but the video will halt and sputter and then quickly try and catch up. This is very annoying and makes watching videos almost unbearable.

---

### Post by arnieboy on 2005-03-25
go to synaptic and search for totem_xine and install that. If it requires the removal of totem_gstreamer allow that. This should solve your problems. Run totem_xine after that and enjoy!

---

### Post by Corey on 2005-03-25
Ugh, I was afraid someone was going to say that. I geuss that means the problem is with Gstreamer? I hate redundently having two backends, and I'd prefer mplayer of xine, but I couldn't get that to run properly either :( Oh well. Guess I can make do with Xine_Totem untill a more stable Gstreamer comes out (hopefully before the final hoary release!)

---

### Post by ACK!! on 2005-03-26
[QUOTE=Corey]Ugh, I was afraid someone was going to say that. I geuss that means the problem is with Gstreamer? I hate redundently having two backends, and I'd prefer mplayer of xine, but I couldn't get that to run properly either :( Oh well. Guess I can make do with Xine_Totem untill a more stable Gstreamer comes out (hopefully before the final hoary release!)[/QUOTE]

Funny thing is when I first installed ubuntu Hoary i had the opposite experience.  Watching movies with gstreamer totem was smoother and I know this is the reverse of most user's experiences btw.  

Totem xine however plays more formats included if you get w32codecs the sorrenson quicktime stuff.  

My totem-xine stutters for about 5 minutes of the movie and then things smooth out for the rest of the film, very weird.

---

### Post by arnieboy on 2005-03-26
a good idea wud be to install all libs and dev packs by searching for "xine" in synaptic.. u often dont know which arcane pack of libs is making ur movie player stutter. for me totem_xine works perfectly... both for dvd's and movie files as such.

---

### Post by v79 on 2005-03-26
I also have poorer performance from totem now that I moved to hoary, but I think it's because I've moved to xorg and enabled the composite and xdamage extensions. xdamage in particular can be slow to update, and moving from windowed to fullscreen dvds is very flaky - often I get a white screen, 1/4 of which shows 1/4 of the fullscreen dvd. Takes over a minute sometimes for the fullscreen to actually, well, go fullscreen.

I remember that RISC OS implemented an xdamage type system back in, ooh, 1991? And it had proper font management, all anti-aliased, in 1992...

V79

---

### Post by bonega on 2005-03-26
Hi.

Totem-Gstreamer works fine once you force gnome to use Alsa as sound output.

system-settings-chooserformultimedia

---

