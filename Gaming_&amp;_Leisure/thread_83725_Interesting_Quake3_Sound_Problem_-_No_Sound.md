---
title: "Interesting Quake3 Sound Problem - No Sound"
date: 2005-10-29
forum: Gaming &amp; Leisure
---

### Post by jtwJGuevara on 2005-10-29
Here's the console output from quake3:

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0xb0acf000 dma buffer
No background file.
----------------------

The line that reads "sound system is muted" is quite peculiar.  I have sound in ever other application.  It is my understanding that quake3 uses oss.  And by the looks of this console message, is it oss that is muted?

---

### Post by jtwJGuevara on 2005-10-29
Amazingly, I'm solving all of my problems the minute I post about them.  Maybe someone can learn from them.

I forgot I have an onboard soundcard and a second soundcard (one that supports hardware duplex).  Quake3's snddevice setting was set to /dev/dsp which is the onboard sound.  I'm using the other soundcard.

What I did was edit ~/.q3a/baseq3/q3config.cfg and changed this line
snddevice /dev/dsp1

and voila!

---

### Post by dfm21 on 2007-06-05
also be sure snddevice is not set in one of your other config files.
to be sure you can start quake 3 with:
```

$PATHTOQ3DIR/quake3 +set snddevice /dev/dsp1

```
You can get a list of available sound devices with
```

ls /dev/*dsp*

```

---

### Post by Riel on 2007-07-01
I tried all 4 of em (adsp, adsp2, dsp, dsp2)

all muted...
in /dev/snd/ are no usable ones?

---

### Post by Riel on 2007-07-02
Noone an idea to get that ' muted '  away?


Maybe one interesting detail:

my sound worked perfect at 1st install.
The only thing I installed afterwards what gave me sound-issue's too, now i think about it, is WINE. No sound there either...

---

### Post by Gen2ly on 2007-07-02
I've just been writing about this in the gentoo linux wiki.  search for it there at

[http://gentoo-wiki.com](http://gentoo-wiki.com)

---

### Post by Riel on 2007-07-05
No options there too.

Can't get it to work, it stay's 'muted'.

other options?

What's with ALSA?
When I use alsa for normal sounds, it works (test).
my own, Cmedia, works too (test).

But no quake.

---

### Post by Riel on 2007-07-05
I installed the OSS sound system, and all worked ...

---

