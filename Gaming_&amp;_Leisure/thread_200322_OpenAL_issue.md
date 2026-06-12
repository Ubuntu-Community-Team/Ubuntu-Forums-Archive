---
title: "OpenAL issue"
date: 2006-06-20
forum: Gaming &amp; Leisure
---

### Post by musther on 2006-06-20
A few days ago I was running Dapper, up to date, and playing a game (bridge construction set) which uses OpenAL for audio.  I had a hard drive failure and have had to reinstall, the game was on my home partition so I thought I'd be fine.  I tried to play it and then remembered that I hadn't installed openAL, so I opened synaptic and searched for it.  I found two packeges with identical descriptions, libopenal0 and libopenal0a.  I tried libopenal0, ran the game, and the game worked, but with no sound.  I noticed this at the terminal:

```
pause_audiodevice stubbed for 0x3
```


So I removed it and tried libopenal0a (with this package I was able to install openAL tools (libalut0), so I did), this time when I tried to run the game I got:

```
./bcs: symbol lookup error: ./bcs: undefined symbol: alutInit
```

So, this must be an openAL problem (at least, I think it must).  The other requirement of the game is SDL, I'm sure this doesn't have anything to do with it though.

Cheers

---

### Post by Abukaspar on 2006-07-12
I had the same issue and looked at the OpenAL documentation.
The reason is that the ALUT symbols are now provided in a separate library: libalut.so. 
The trick is to inform your binary to load the appropriate library by typing this in your terminal:

LD_PRELOAD="/usr/lib/libalut.so" ./bcs

Now your game should start normally.

---

