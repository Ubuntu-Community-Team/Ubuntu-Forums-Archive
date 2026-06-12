---
title: "No sound in games"
date: 2005-08-12
forum: Gaming &amp; Leisure
---

### Post by infornography on 2005-08-12
Hi,

I'm having trouble getting the sound to work in any games for Hoary. Sound works fine for all the system sounds, programs like gaim, and I can play mp3's without issue. But for some reason games don't work.

I have tested the sound with Clan Bomber, Tux Racer, Frozen Bubble, Super Tux, Battle for Wesnoth, and even Zsnes with several roms, and get nothing. Can anybody give me a reason why its working for some things and not others?

Also, I don't know if it makes a difference. But its not that there is sound and I just cant hear it. The programs refuse to make sound at all, for example on Frozen Bubble the volume control is disabled.

---

### Post by Toddy on 2005-08-12
Try this:

sudo apt-get install libsdl1.2debian-all

---

### Post by infornography on 2005-08-12
I'll be damned. It worked.

I can't believe it was that easy, I was expecting something of a struggle. Thank you very, very much.

EDIT: Perhaps I spoke too soon. while it did fix most of the games, Wesnoth, Super Tux and Clan Bomber still don't work.

---

### Post by jyank on 2005-08-12
Try typing this into a terminal

```
killall esd
```

That possibly might turn off the sounds for gaim/your music player pending what output you use.

If that works and you're done playing the game just type 

```
esd
```

back into a terminal and it should reload it.

---

### Post by jdodson on 2005-08-12
Yeah the killall esd works on my work laptop, my home desktop has a bitchin soundcard so its not an issue, I just turned off everything that wasnt ALSA.  Works well.  Anyways, check out my sound thread here: [http://ubuntuforums.org/showthread.php?t=42492](http://ubuntuforums.org/showthread.php?t=42492)

Some people have found that install polypaudio(sp?) helps them out, didnt work for me though.

---

