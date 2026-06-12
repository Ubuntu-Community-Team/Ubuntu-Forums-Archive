---
title: "No sound SBLive and ALSA"
date: 2008-12-10
forum: Desktop Environments
---

### Post by coombesy on 2008-12-10
I am getting a weird problem... there is no sound coming from any of my media players.

I checked the sound properties (system->preferences->sound) and all the test buttons work (except sound capture but i presume thats for a mic test) but when i try play a song there's no sound.

The sound used to work perfectly, until I started messing with 'alsamixer' and now I can't get it back. I've tried turning up everything in the mixer but am i right in saying that you shouldn't do this? That there are some volumes that should be muted?

If i'm getting sound from the 'test' button through the speaker then the problem must lie with a sound channel being muted,

ubuntu 8.04tls
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
	Subsystem: Creative Labs CT4780 SBLive! Value
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at d800 [size=32]
	Capabilities: <access denied>

---

### Post by coombesy on 2008-12-10
Solved? The sound came back! All i did since my last post is use firefox and try rhythmbox, so maybe, something was trying to hog the channel for media players and it got kicked of by rhythmbox.

But I can promise you over the last two days I have tried every program I have ;)

If i discover the cause i'll post my results back here.

---

