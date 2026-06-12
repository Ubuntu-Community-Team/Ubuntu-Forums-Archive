---
title: "No sound from rhythmbox"
date: 2009-04-13
forum: General Help
---

### Post by Gorgapor on 2009-04-13
I've seen alot of similar problems reported with rhythmbox, but none seem to match my situation.

[LIST]
[*]No sound output when I press the play button
[*]Correct sound output in totem, vlc, and all other programs
[*]Volume slider is up in rhythmbox and in the mixer
[*]The time slider moves, and the time counts up correctly
[*]No error output in the console
[*]Using pulseaudio, and Ubuntu 8.10
[/LIST]

I'm out of troubleshooting ideas to try, anyone got any more?

---

### Post by memories on 2009-04-13
Have you dug through the rythmbox preferences? Also try using the Pulse equivalent to "alsamixer" and make sure the correct sliders are audible or muted. 

2 rants.. first, rhythmbox sucks. It's bloated, has no features and is slow. I've been using it for years just because it was the default player with ubuntu/gnome. I loved Amarok but it's not natively for Gnome (it's for KDE), and I figured I had no choices, but we do. 

Yesterday I found "Listen" and "Exaile" for Gnome and their both really good. Listen crashed once when I tried playing a 60 min mp3.. very annoying, but it hasn't happened again (with any mp3 including the one that crashed it first time around). Exaile has been pretty good. Both are better than rhythmbox IMO. Also IMO, rhythmbox should not be the default player, or it ubuntu should come supplemented with some other big players like Exaile. All players need equalizers ... 

and, pulse is awful. It's broken with skype and many other apps. The best thing I did was removing it completely and reverting back to ALSA. There was a thread on these forums on how to remove it. Now everything works perfectly, though I had to switch settings in some apps after I removed it.

---

