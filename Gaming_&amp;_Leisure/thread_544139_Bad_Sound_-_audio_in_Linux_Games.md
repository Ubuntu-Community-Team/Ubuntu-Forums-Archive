---
title: "Bad Sound - audio in Linux Games"
date: 2007-09-05
forum: Gaming &amp; Leisure
---

### Post by Ioky on 2007-09-05
I own a few natural Linux Game such as Unreal Tournament 2004, NeverWinter Night, and Heroes of Might and Magic. However, for most of them. the Audio and Sound doesn't work out right. skippy, and some bitting sound. I just sound every bad. the only game that work ok with the sound is UT 2004. I wonder any one know what problem I am facing. and how to fix it. All the game I mention are Linux Version Game, I didn't use Wine for it. well I don't have to, so

I mean if that is cause by my hardware, I can only get a low profile sound card, but that is about it. because my case is really small. so if you know any good one that work with linux, please let me know. You are the best haha and thanks for the help

Thanks.....

---

### Post by drkknight on 2007-09-06
Do the games run well otherwise? I've had problems with Unreal Tournament and Never Winter Nights too. The games ran fine, but I had to disable ALSA in order for the sound to work at all. Try that out if you are using ALSA maybe.

---

### Post by Cappy on 2007-09-06
You may need to move your sound libraries from /usr/lib to your game directory if it is using an old version of the sound library. A recent guide to installing a game should probably cover this.

For instance, it may be something like libSDL-1.2.so.0 you may need to copy over. It could also be that you need to switch your computer to OSS sounds instead if you have a really really crappy sound card. I remember seeing a few misc fixes for this problem in the gaming forums when it was none of the above.

---

### Post by Ioky on 2007-09-06
Wow, Nice that works Great. the lib thing really work for neverwinter night SWEET.. haha 
Thanks so much. However, Hero of Might and Magic still wouldn't work, well it doesn't have a libSDL-1.2.so... lib file at all. so that is like I have no where to fix it. 

Once more thing, drkknight, i think you should give it a try too. hope that is going to work for you as well. 

Thanks all your help after all

---

### Post by Ioky on 2007-09-07
Finally!! Finally!! I get all the sound working. not complete perfect but work way better then before. Neverwinter Nights works perfect, and now even Heroes of Might and Magic work fine. still have a little bit of Bitting sound going on when music are playing, it might be some Mp3 decoding problem. sense the game is use Mp3 for music, i don't think I can done much about it. so yeah. If anyone for you have the same problem as I i would like to share, the way it work for me with you.

---

### Post by drkknight on 2007-09-07
I'm going to have to keep this in mind for sure.

---

### Post by JoSch on 2008-02-12
@loky cant figure out what you did in the case of homam which libs do you copy?

I have a similar problem with heroes of might and magic 3 - it uses OSS but my ubuntu uses alsa.
switching sound output in the volume control doesn't help and using aoss doesn't either.
the sound stays very choppy but I dont know why because it's a 3Ghz core2duo

---

