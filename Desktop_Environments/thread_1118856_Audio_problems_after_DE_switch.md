---
title: "Audio problems after DE switch"
date: 2009-04-07
forum: Desktop Environments
---

### Post by achilleas.k on 2009-04-07
Recently I switched from Gnome to xfce and I loved it. I'm using 8.10 Intrepid 64bit and I had originally installed plain Ubuntu (Gnome) and simply installed xubuntu-desktop in order to try out xfce. I'm also keeping Gnome around for the "just in case" factor and because I keep using some of the Gnome apps (mostly panel applets).

My only big problem now is with sound. In general, sound is working fine. When I'm watching a video there's no delays of any kind for instance. My problem is with audio players such as Rhythmbox and Listen. When I'm listening to music using these players, there are hangs when starting a song or when switching from one song to another. When the song starts playing it carries on fine. I timed it and it seems it always hangs for 20 seconds. During that time the software is unresponsive in general.
A somewhat related problem is with aMSN. When I receive a message, I get the appropriate notification sound a considerable amount of time after the message (could be 20 secs as well, haven't timed it).

These delays and hangs do not occur when I'm using Gnome even after the xubuntu-desktop installation.

What could be causing this? It wasn't much of a problem when it was only aMSN, but with Rhythmbox it's pretty annoying when you're skipping through songs and it takes 20 secs for each one to start to playing.

---

### Post by achilleas.k on 2009-04-08
Is it possible that when I'm using XFCE, a different decoder is used for MP3 files than when I'm using Gnome and that decoder is problematic?

---

### Post by achilleas.k on 2009-04-09
Sorta solved the problem, though I dunno if I caused any damage in the process. I saw that when I tried to play MP3 files in mplayer it hanged for a bit and then it gave a message along the lines of "[pulse audio] could not connect to server". Now I'm sure there is a way to repair this properly, but I instead removed pulse and reverted back to alsa and everything seems to be working well.

---

