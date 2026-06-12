---
title: "Sound not working in games (ppracer, neverball, etc)"
date: 2006-02-22
forum: Gaming &amp; Leisure
---

### Post by BeatBoxRocker on 2006-02-22
I hope i didnt choose the wrong section :)

I have downloaded some games but i cant get the sound to work with them. The other programs like Amarok or xmms works well.

I Have been searching in the forum and tried some possible solutions but i cant fix this. I have installed libsdl1.2debian-all, killed esd before running the game from console, closed any program that were playing music/sound...

I have a Sound Blaster Live 5.1 and an integrated AC'97 but the first one is selected for the sound (editing the /etc/asound.conf).

Any help is apreciated! Saludos!

---

### Post by qwerty-ubuntu on 2006-02-27
Hi, I was having this problem and also tried installing libsdl1.2debian-all, however this didn't work.  I read somewhere else to install libsdl1.2debian-esd, this uninstalls libsdl1.2debian-all and has fixed sound in games for me such as barrage and cube and all others I have tried.

Hope that helps

---

### Post by hanspb on 2006-03-20
I had the same problem, and I found out I had to kill esd, the sound daemon while playing the game. I made a bunch of small scripts using this template:

```
killall esd
name_of_game
esd &
```

This kills esd, starts the game and restarts esd when the game is finished. Remember that the "&" in the last line is important, as it runs esd in the background.

---

