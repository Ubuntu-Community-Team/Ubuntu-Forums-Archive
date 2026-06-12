---
title: "Totem still wont play any avi codecs"
date: 2005-06-24
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-24
Even tho they're installed as per ubuntu guide

I do not know why, but VLC plays some mpegs jerky and that's not ok. I wanna use totem! but it just doesn't play anything

And all the help on the subject is in foreign. Lets have an English one

---

### Post by WAM on 2005-06-25
Same problem. Well, it plays the audio but not the video. I just use VLC.

My biggest problem is that for some reason Ubuntu/Nautilus/I don't know where the problem is from can't differentiate between video .ogg and audio only .ogg formats.

---

### Post by Darrena on 2005-06-25
[QUOTE=WAM]Same problem. Well, it plays the audio but not the video. I just use VLC.

My biggest problem is that for some reason Ubuntu/Nautilus/I don't know where the problem is from can't differentiate between video .ogg and audio only .ogg formats.[/QUOTE]
 Have you installed w32codecs?   Totem-gstreamer that comes with Ubuntu by default doesn't play all formats so you may want to install totem-xine as well.

Do do this type from a terminal:

sudo apt-get install w32codecs
sudo apt-get install totem-xine

---

### Post by Dave_is_sexy on 2005-06-25
Yeah
[HTML]
dave@D5:~$ sudo apt-get install w32codecs
Password:
Reading package lists... Done
Building dependency tree... Done
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
dave@D5:~$[/HTML]

---

### Post by stefanoaguiar on 2005-06-28
While installing toten-xine it removes the gstreamer package, onde of those meant to be installed by the HowTo. Anyway, it worked and Totem here is playing everything nice and easy.

Thanks, guys.

---

