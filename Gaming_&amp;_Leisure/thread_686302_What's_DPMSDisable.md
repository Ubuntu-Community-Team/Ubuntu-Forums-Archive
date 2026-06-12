---
title: "What's DPMSDisable?"
date: 2008-02-03
forum: Gaming &amp; Leisure
---

### Post by BigSilly on 2008-02-03
I don't know why, but for some reason the audio seemed to disappear yesterday on a couple of games programs I use on Ubuntu, chiefly Secret Maryo Chronicles and SDLMame. I noticed when I ran smc (Secret Maryo) from a terminal that I was getting a "No available sound device" error. I had a look around these forums, and someone seemed to be suggesting that I needed to install a sound driver with complete SDL abilities, so I installed libsdl1.2debian-all, instead of the libsdl1.2debian-oss that I had previously.

Lo, this seemed to fix matters, and I now have audio on these programs. However, I'm now getting this error from the terminal:

```
Last known SDL Error : Failed loading DPMSDisable: /usr/lib/libX11.so.6: undefined symbol: DPMSDisable
```

What is this, and is it something I should be worried about? The game (smc) seems to run fine, but the terminal clearly says not. Your help is much appreciated.

---

### Post by jnylen on 2008-02-08
> **BigSilly said:**
> I don't know why, but for some reason the audio seemed to disappear yesterday on a couple of games programs I use on Ubuntu, chiefly Secret Maryo Chronicles and SDLMame. I noticed when I ran smc (Secret Maryo) from a terminal that I was getting a "No available sound device" error. I had a look around these forums, and someone seemed to be suggesting that I needed to install a sound driver with complete SDL abilities, so I installed libsdl1.2debian-all, instead of the libsdl1.2debian-oss that I had previously.

Lo, this seemed to fix matters, and I now have audio on these programs. However, I'm now getting this error from the terminal:

```
Last known SDL Error : Failed loading DPMSDisable: /usr/lib/libX11.so.6: undefined symbol: DPMSDisable
```

What is this, and is it something I should be worried about? The game (smc) seems to run fine, but the terminal clearly says not. Your help is much appreciated.I get this error too (on Gutsy with smc) but the game runs fine.  I don't think it's a big problem - Linux seems to spit out messages like that pretty often for me but if everything still works I tend not to care too much.  But you could always [http://www.google.com/search?q=sdl+dpmsdisable](http://www.google.com/search?q=sdl+dpmsdisable) .

---

### Post by jnylen on 2008-02-08
Oh, also, what are some other good games that are in the package manager, if you know of any?

---

### Post by aksommerville on 2008-02-18
That warning about DPMSDisable is what SDL kicks out if you ask it for its most recent error code, and there haven't been any errors. Must be a little bit of sloppy coding on SMC's part, but you can safely continue to ignore it. :)

---

