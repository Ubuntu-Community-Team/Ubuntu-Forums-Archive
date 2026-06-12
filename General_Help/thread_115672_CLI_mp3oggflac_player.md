---
title: "CLI mp3/ogg/flac player"
date: 2006-01-11
forum: General Help
---

### Post by ohman on 2006-01-11
I'm currently running a server install of ubuntu on my file server, and I would like to start using it to play mp3s as well.  The reason is that I would prefer my nice, fancy receiver + speaker combo to handle the sound versus my crappy laptop speakers (in addition to being untethered with regards to my laptop).

What I am looking for is a command line only mp3 player, preferably with either a ncurses interface OR some sort of remote administration via web (the later would be simply put, amazing).

I have come across snd123, which will decode almost everything under the sun, but is lacking with regards to an interface.  Any ideas?

---

### Post by zoiks on 2006-01-11
Try mp3blaster

---

### Post by psychicdragon on 2006-01-11
Look into mpd (the music player daemon). There are both command-line and gui frontends for it, and it keeps playing when you exit from X.

---

### Post by nkhansen on 2006-01-11
I have put up an mpd server. It was not that hard, and there is both web interfaces, and remote clients. It is relatively easy to set up (as far as I can remember, but I tend to forget these things. Documenta-what?).

---

### Post by ohman on 2006-01-11
nkhansen and psychicdragon:  Thanks, mpd sounds like exactly what I was looking for.

---

### Post by ScreemingBlue on 2006-01-11
Add in NCMPC and you have an ncurses app to control mpd. I use mpd with ncmpc to create playlists and control play, vol etc. Very cool. The latest version of MPD is also a source for ICECAST2 streaming server so you can listen and control your music from anywhere using NCMPC over SSH and all via terminal. Excellent.... see this link [http://mpd.wikicities.com/wiki/Main_Page]("http://mpd.wikicities.com/wiki/Main_Page")

---

