---
title: "Movie Player won't play dvd, but Dragon player will"
date: 2008-02-05
forum: Desktop Environments
---

### Post by Jeanpaul145 on 2008-02-05
I have a couple of dvd's (the godfather trilogy) that Movie Player won't play, and my mother's old dvd player won't play them either. Movie player accepts the dvd and starts as if it wil play, but the I see *only* artifacts in the playback, no sound, and no recognisable movie footage. The dvd player even says there is no dvd present.
Oddly enough, when I try to play these very same DVD's with Dragon player, it plays them perfectly (I have to adjust the brightness a little, but that's about it).

How come Movie player won't play the dvd, let alone play it acceptably?
That my mother's dvd player won't play it **could be** because it's old (compatibility problems come to mind) but I like to think the gnome software is a little more up to date?

---

### Post by Jeanpaul145 on 2008-02-05
I've also tried a fresh start with xine based players as shown on [this community site]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").
gxine works perfectly.
I'm still interested to know why Totem won't play the dvd's, seeing as how it's automatically started when I insert a dvd ( and I don't really want to change that).

---

### Post by Jeanpaul145 on 2008-04-04
anybody?

---

### Post by warp99 on 2008-04-04
Did you install libdvdread3 and libdvdcss2 to read encrypted DVDs? Put the DVD in the tray, open a teminal and type the following:

```
totem dvd://
```

What is the output? Does it decode properly and start playing? Is the video blank or choppy?

---

