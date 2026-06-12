---
title: "Heroes Of Newerth, pulseaudio 5.1 choppy sound fix ubuntu 9.10"
date: 2009-11-10
forum: Gaming &amp; Leisure
---

### Post by Anril on 2009-11-10
**Platform**:
Ubuntu 9.10 amd64 with audigy4 soundcard for game Heroes Of Newerth (beta).

**Bug description**:
Choppy sound in game if soundcard is set to 5.1 (6 speakers)

**Fix**:
In file */etc/pulse/daemon.conf* change

[I]default-fragments = 8
default-fragment-size-msec = 1[/I]0

to

[I]default-fragments = 4
default-fragment-size-msec = 5[/I]

Those are also highest values i can set without getting choppy sound in game.

---

### Post by Vadi on 2009-11-11
Thanks, I'll give it a try.

I found that using a special build where I was modify it's sound buffer from default 512 to 4096 worked (although player voip was played back to me twice then, second time in a broken manner).

edit: tried, didn't have a chance to play yet - but with the default sound buffer size, this does work for fine sound in the lobby.

---

### Post by Anril on 2009-11-12
well these options give good sound in game but it gives poor sound while watching tv so every time before i start HoN i swich soundcard from 5.1 to Stereo

---

### Post by Vadi on 2009-11-12
This didn't help much. Worked fine one match, second match choppy, third match no sound.

Back to 4096 buffer size and double-playback of voip voices :\

---

### Post by Anril on 2009-11-13
Well duno if u get same problem but if i dont disable all sounds in game i get kinda laggy graphic.

I took this to game forum: [http://forums.heroesofnewerth.com/showthread.php?p=575114#post575114]("http://forums.heroesofnewerth.com/showthread.php?p=575114#post575114")

---

