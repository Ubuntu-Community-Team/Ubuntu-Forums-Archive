---
title: "Tremulous dropping sound and freezing on exit - pulseaudio?"
date: 2008-04-09
forum: Gaming &amp; Leisure
---

### Post by smekis on 2008-04-09
Having an annoying problem in tremulous. After a while of gameplay (seems random, sometimes a couple of seconds and sometimes more than 10 min) the sound just stops and I'm getting a "dropping sound" message (in game).

When I try to exit the game (using the in game menu) the game freezes. If I (by logging in from Ctrl-Alt-F1) killall tremulos, I can see my desktop but in the tremulous resolution and with mouse and keyboard not responding.

When I "killall Xorg" and relogin everything is back to normal.

I figured this as much as this might have to do with me changing to pulseaudio a while back...

Otherwise I use the preset settings in Ubuntu 7.10 Gutsy.

Any ideas?

---

### Post by Azzco on 2008-05-12
I'm just going to confirm this (4 weeks later) on Hardy Heron (kubuntu though).

I tried installing libsdl1.2debian-all as well (A google search hinted it) but that didn't help either. "padsp tremulous" doesn't seem to do anything special either..

I hope a fix will turn up so that I can join my class mates again :p

---

### Post by Azzco on 2008-05-14
I went to the tremulous irc channel and got some help.
Just thought I'd post that after installing libsdl1.2debian-esd tremulous (and frets on fire) works for me flawlessly again

---

### Post by lordcap90 on 2008-05-21
I have a similar problem with warzone 2100 and chromium b.s.u. with chromium, the sound stops a few seconds after playing and when trying to exit normally, the game freezes and has to be killed. same goes for warzone. I use to just turn off pulseauido, but without it, the sound has now become choppy for some reason. I have bean looking for an answer to this problem with no avail ](*,)

---

### Post by billybag on 2008-08-15
> **lordcap90 said:**
> I have a similar problem with warzone 2100 and chromium b.s.u. with chromium, the sound stops a few seconds after playing and when trying to exit normally, the game freezes and has to be killed. same goes for warzone. I use to just turn off pulseauido, but without it, the sound has now become choppy for some reason. I have bean looking for an answer to this problem with no avail ](*,)

I have the same exact problems with warzone. any fix yet?

---

### Post by lordcap90 on 2008-08-16
Check out [this link]("http://wiki.archlinux.org/index.php/PulseAudio#Configuration_of_OpenAL_for_PulseAudio") it worked for all my games that use the OpenAL API including warzone and chromium B.S.U.

---

### Post by clnaveen on 2008-10-28
This worked for me... but this locks up the sound card and other apps are muted... 


funnily enuf the games bypass pulseaudio instead of using it... the game doesn't show up on the pa manager.

---

