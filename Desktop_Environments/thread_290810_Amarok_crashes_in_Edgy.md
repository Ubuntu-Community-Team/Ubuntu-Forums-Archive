---
title: "Amarok crashes in Edgy"
date: 2006-11-01
forum: Desktop Environments
---

### Post by jgio on 2006-11-01
Hello to everyone,

I installed amarok from apt-get and when i double-clicked an mp3 file to play a window opened "Amarok doesn't have mp3 support. Download now?" i clicked yes. But since then it crashes? Any ideas?

(ubuntu edgy)

---

### Post by kkinder on 2006-11-01
I take it Amarok was working fine before Edgy? I've noticed KDE apps are just generally not stable in Edgy too, *especially* on an upgraded system. (Fresh installs seem to do much better for some reason...)

To get mp3 working, install the following packages:

> sudo apt-get install libxine-extracodecs w32codecs libarts1-mpeglib  libarts1-xine libakode2-mpeg

See [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats) for more information on that.

---

### Post by Arby on 2006-11-01
That is odd and shouldn't happen, do you see any error messages?

As a work around you could try adding mp3 support yourself using these instructions: [https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29)

The instructions there are for 6.06 (Dapper) but they work the same with 6.10 (Edgy)

---

### Post by scotty32 on 2006-11-01
> **jgio said:**
> Hello to everyone,

I installed amarok from apt-get and when i double-clicked an mp3 file to play a window opened "Amarok doesn't have mp3 support. Download now?" i clicked yes. But since then it crashes? Any ideas?

(ubuntu edgy)


worked fine for me (though i did a fresh install)

i had problems installin mp3 support - as it didnt install it, just told me it did for sum reason, so i restarted amarok thinkin it installed but it didnt

it hasnt crashed on me yet

*edit* i just noticed the post above me, i enabled all repos before i installed amarok (or even mp3 support) am guessing you'd have to enable the right repo for it to work otherwise it'll fail

---

### Post by Arby on 2006-11-01
> **scotty32 said:**
> 
*edit* i just noticed the post above me, i enabled all repos before i installed amarok (or even mp3 support) am guessing you'd have to enable the right repo for it to work otherwise it'll fail

Yes - good catch. Info on repositories here [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories). If you haven't enabled the extra repositories that might be what caused amarok to crash when it looked for mp3 support

I'd also like to second scotty's comment on stability. I've installed kubuntu edgy and it's been no trouble after a few install problems caused by my own incompetence

---

### Post by jgio on 2006-11-02
Thnx guys problem SOLVED ;)......

---

### Post by dheerajsp on 2006-11-02
i have the same problem. it plays mp3 files, but amaroK and Kopete crash a lot actually, and for no particular reason too!

---

### Post by reyfer on 2006-11-02
Well I didn't have any problems with Amarok 1.4.3 when I upgraded to Edgy, and now I'm running 1.4.4 and still no issues, Amarok is working great!!!

---

