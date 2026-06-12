---
title: "tvtime color/channel off"
date: 2006-01-20
forum: Desktop Environments
---

### Post by crispy_420 on 2006-01-20
I've done it before but can't seem to remember how to now. As one of the major bugs in tvtime the tuner will not display the correct channel(by one) and color will be dull. I want it to report as tuner 2 but keeps reporting as tuner 5.

I've followed the instructions as per tvtime and can't seem to get it to work. What files should I modify?

My tv tuner is bt878 based. Just in case I missed something ask me for more details.

---

### Post by crispy_420 on 2006-01-20
Anyone else have this problem? Or am I alone?

---

### Post by Omnios on 2006-01-20
I tryed tv time a long time ago till I found Zapping and found it more desirable.

---

### Post by crispy_420 on 2006-01-20
No matter what program I use it is the same problem. 

color dull(black and white with some color) and channels off be one

The point of my post was to solve the essntial problem to cover actual problem.

My card is always reported as a tuner=5 when I want it to report as tuner=2.

What file do I need to modify/change to fix this? I had it on another install but don't remember how I did it.

---

### Post by desperate_cry on 2006-01-21
I have the same problem, one channel showing as you described and channel is that i last opened from windows...

What can i do?

---

### Post by crispy_420 on 2006-01-23
I solved my problem but if you don't have the same card I don't know if if will help you:

[FOUND HERE]("http://www.ubuntuforums.org/showthread.php?t=107932&highlight=bttv")

If you need to know what to put in the tuner part try here:

[BTTV cardlist]("http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV")

Tuner is for your region (NTSC, PAL, etc.), I think. This is what I know so far:

```
NTSC...tuner=2     PAL...tuner=5
```

If your card has radio tuner, than use radio=1 and radio=0 for none.

No idea what pll=1 does but my card works now.

Also found this detailed list info here:

[_BTTV Driver Home?_]("http://linux.bytesex.org/v4l2/bttv.html")

and here:

[Tuner List]("http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm")

---

### Post by desperate_cry on 2006-01-30
Thanks...

It works.

I love you :)

---

