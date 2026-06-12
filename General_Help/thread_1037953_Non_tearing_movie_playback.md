---
title: "Non tearing movie playback"
date: 2009-01-12
forum: General Help
---

### Post by Yashiro on 2009-01-12
I generally use Totem for watching divx/h264 encoded movies. The long standing problem I have  is tearing during playback.
I have a Radeon 4850 using fglrx drivers. The drivers work and are stable. Xv hardware overlay works fine as long as Compiz is disabled.
Vsync is enabled in every possible location yet movies (and games) exhibit tearing.

I'm well aware that X/vsync is a long running Linux oddity and my well be resolved in a few months. (EXA, UXA, DRI, GEM, TTM changes etc)

But in the meantime... "It's the drivers!" you say, but the point of this post is that it isn't, primarily. 

After countless hours of messing about I've found one player that has no tearing. *XBMC for Linux.* However, XBMC has it's own issues. It doesn't work with pulseaudio and is also prone to random crashes.

What it the point of this ramble? I'm curious how XBMC has eliminated this tearing and if it can be ported to Totem or Mplayer. (Or perhaps there is a command I can pass to mplayer that is equivalent to the 'always enable vsync' within XBMC)

---

### Post by Titan8990 on 2009-01-12
I personally have had no issues with VLC. You should give it a try.

---

