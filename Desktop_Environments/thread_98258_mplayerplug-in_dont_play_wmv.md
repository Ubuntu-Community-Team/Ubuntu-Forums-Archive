---
title: "mplayerplug-in dont play wmv"
date: 2005-12-02
forum: Desktop Environments
---

### Post by nix4me on 2005-12-02
Hi,

I have mplayerplug-in 3.11 installed and when i click on a wmv file in firefox it does not play in mplayerplug-in.  Instead it opens a window and asks which player to use.

mpg works fine.

Does the mplayerplug-in play wmv's?

nix4me

---

### Post by kperkins on 2005-12-02
It does if you have the codecs installed (w32codecs), and I don't remember where to get them, although there's a tutorial around the forums, somewhere.

---

### Post by nix4me on 2005-12-02
I have the w32codecs installed.

All formats of video work fine except wmv.

nix4me

---

### Post by discord on 2005-12-02
wmv works for me with the plugin. Maybe it only works with some wmv files. Have you tried others? If it does not work with either i suggest you remove mplayer and reinstall it maybe try the automatix installer script.. you can find it here or google via search...

---

### Post by kperkins on 2005-12-02
[QUOTE=nix4me]Hi,

I have mplayerplug-in 3.11 installed and when i click on a wmv file in firefox it does not play in mplayerplug-in.  Instead it opens a window and asks which player to use.

mpg works fine.

Does the mplayerplug-in play wmv's?

nix4me[/QUOTE]
I misunderstood your question.  Firefox does the same for me, some wmvs play in the plugin, and some don't for some reason.  I assume it's the way they've been encoded.  I just choose gmplayer to play them, and it works fine.  (I seem to be having a problem right now with FF remembering my preferences, so I have to do that every time, but it's a minor annoyance, that I'l fix when I get to it--I think ithas something to do with the factthat I have FF.5 in /opt.)

---

### Post by nix4me on 2005-12-03
Well so far, my mplayerplug-in will not play any streaming wmv.  It always asks for external program.

In firefox it asks for a player, in epiphany it automatically plays in totem.

I think maybe there is a misconfiguration of the file types that are supposed to get played with the plugin.  Here is my /etc/mplayerplug-in.types file.

video/mpeg:mpg,mpeg:MPEG;
audio/mpeg:mpg,mpeg:MPEG;
video/x-mpeg:mpg,mpeg:MPEG;
video/x-mpeg2:mpv2,mp2ve:MPEG2;
audio/mpeg:mpg,mpeg:MPEG;
audio/x-mpeg:mpg,mpeg:MPEG;
audio/mpeg2:mp2:MPEG audio;
audio/x-mpeg2:mp2:MPEG audio;
audio/mpeg3:mp3:MPEG audio;
audio/x-mpeg3:mp3:MPEG audio;
audio/mp3:mp3:MPEG audio;
video/mp4:mp4:MPEG 4 Video;
application/x-ogg:ogg:Ogg Vorbis Media;
audio/ogg:ogg:Ogg Vorbis Audio;
application/ogg:ogg:Ogg Vorbis / Ogg Theora;
video/fli:fli,flc:FLI animation;
video/x-fli:fli,flc:FLI animation;
video/vnd.vivo:viv,vivo:VivoActive;
application/x-nsv-vp3-mp3:nsv:Nullsoft Streaming Video;

I don't see wmv in there at all.

Can someone please that has a working mplayer/mplayerplug-in compare their /etc/mplayerplug-in.types file to this.

nix4me

---

### Post by mlmurray on 2005-12-03
You're not alone.  I've been noticing the exact same behavior as well.

---

### Post by nix4me on 2005-12-03
I have finally given up on mplayer and mplayerplug-in.

It just doesn't work

I will stick with totem and w32codecs.  Launches externally but works 100%.

nix4me

---

### Post by sifion on 2008-01-17
> **nix4me said:**
> 
Can someone please that has a working mplayer/mplayerplug-in compare their /etc/mplayerplug-in.types file to this.

nix4me


i'm having the same problem here... i would just like to know how to make a line for the wmv...

see ya...

---

