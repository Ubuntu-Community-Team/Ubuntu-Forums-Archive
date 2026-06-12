---
title: "Crackly sound in XMMS/Beep"
date: 2005-07-25
forum: Desktop Environments
---

### Post by absinthe on 2005-07-25
Hey :)

My Ubuntu system is wonderful, however I have only one issue:

Beep-media-player, when playing music, will randomly make the sound distort
and crackle. To fix it all I have to do is pause/unpause but it is annoying.

Help!

---

### Post by charlieg on 2005-07-26
I remember XMMS doing this.  It seemed to sacrifice sound quality if it thought there wasn't enough computing power available to maintain it - i.e. better to crackle than to play choppily.

I'm not sure how to remedy this for XMMS or Beep.  I can only recommend you try one of the other players.  There's some good options:
[list][*]**Rhythmbox**
This is a good player for Gnome with a nice library browsing interface for choosing your music
[*]**Muine**
This is a nice player with a simple UI for Gnome
[*]**Amorak**
Probably the best music player but aimed at the KDE desktop (so ideal if you're using Kubuntu)[/list]
Hope that helps.

---

### Post by Hamman on 2005-07-26
[QUOTE=absinthe]Hey :)

My Ubuntu system is wonderful, however I have only one issue:

Beep-media-player, when playing music, will randomly make the sound distort
and crackle. To fix it all I have to do is pause/unpause but it is annoying.

Help![/QUOTE]
 What output plugin are you using? OSS, ESD, ALSA?

---

### Post by absinthe on 2005-07-26
[QUOTE=Hamman]What output plugin are you using? OSS, ESD, ALSA?[/QUOTE]

ALSA

---

### Post by Pendergast on 2005-07-26
[QUOTE=absinthe]Beep-media-player, when playing music, will randomly make the sound distort and crackle. To fix it all I have to do is pause/unpause but it is annoying.[/QUOTE]Are you sure BMP does it at random? I also have this problem. As for me, it does only occur while I navigate on websites including flash media. Can you rule out that correlation for yourself?

---

### Post by GreatestGravity on 2005-07-27
Well, I seem to have a crackly problem in XMMS - but only when it's set to maximum volume. Back in winamp, I'd have the winamp-volume-control set at maximum and control everything with the system volume control (it was easier to access). Here, if I set the XMMS volume to maximum, it becomes crackly.

---

### Post by absinthe on 2005-07-29
[QUOTE=Pendergast]Are you sure BMP does it at random? I also have this problem. As for me, it does only occur while I navigate on websites including flash media. Can you rule out that correlation for yourself?[/QUOTE]

Well, you have halfway figured it out for me. It happens in flash websites, yes.

However, it also happens sometimes when I run synaptic and install programs
sometimes when I'm browsing files. Just random, random, random.

I'm using libesd-alsa0, and I followed the how-to that sets that up so my soundcard can play multiple sounds at once, beep/xmms is the only program to randomly start crackling like this.

---

