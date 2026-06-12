---
title: "Mangler and Wolfenstein Enemy Territory (with et-sdl-sound)"
date: 2012-05-17
forum: Gaming &amp; Leisure
---

### Post by kr0n1x on 2012-05-17
Hi, I got a problem with these two applications.
Mangler is a linux native Ventrilo client.
Wolfenstein Enemy Territory... well no description is needed :)

If I run Mangler, it works. I can talk to people and I can hear other people.

If I quit Mangler and I run ET (with ./et-sdl-sound script), I can hear the game sound.

If I run Mangler and then ET, I will just hear ET sound, but Mangler will like... hang. The moment i quit ET, I will receive all the audio (queued while ET was active) coming from my mates on Mangler/Ventrilo.
Anyway, my friends were able to hear me while I was into the game. So the only thing which doesn't work is that I can't hear my friends while I play.

So I can just use one of the two applications at a time.

I'm on Debian Squeeze 64 bit, I'm posting here on Ubuntu forums because probably the solution would work either, and Ubuntu probably has more players ;)

Ah... more details: I tried running et-sdl-sound with esd, alsa, and pulse as SDL_AUDIODRIVER. Only alsa gives me audio, the others don't work.

I use Pulse as my audio server.

Thanks

EDIT: what my terminal says when I run ET with...
et only: [http://ideone.com/5mVZS](http://ideone.com/5mVZS)
et-sdl-sound with esd: [http://ideone.com/jZBz9](http://ideone.com/jZBz9)
et-sdl-sound with alsa (the only working): [http://ideone.com/6MciC](http://ideone.com/6MciC)
et-sdl-sound with pulse: [http://ideone.com/YDrtF](http://ideone.com/YDrtF)

lspci:
```
pasqoo@5742zg:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
```

---

