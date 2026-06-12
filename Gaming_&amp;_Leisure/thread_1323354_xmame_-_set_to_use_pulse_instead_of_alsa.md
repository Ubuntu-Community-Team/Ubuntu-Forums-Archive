---
title: "xmame - set to use pulse instead of alsa?"
date: 2009-11-11
forum: Gaming &amp; Leisure
---

### Post by dchurch24 on 2009-11-11
Hi all,

I recently installed 9.10 and Myth 0.22 on my 'living-room' box.

I also wrote a series of scripts to allow me to play music (through vlc-telnet) from anywhere on my network by streaming the file to whichever machine was 'listening'.

To start with this meant that if MythTV was running (although only in the menu), then vlc couldn't play the sound.

Then I found a EXPERIMENTALLY_ALLOW_PULSE=1 that allows both to access the sound card.

I just installed MythGame and xmame. I started up an old classic and it worked straight away - and the sound was working.

I then tried a rom that xmame didn't like and didn't play. I went back to the other, and I haven't had sound since.

MythTV sound works fine if I play a film or run live-tv - and my scripts still work to tell vlc to play a song.

I can't figure out how to get xmame sound working again.

I ran xmame on it's own (outside of MythGame) and there is still no sound. I noticed in the output this:

```

info: set to 16bit linear stereo 441000Hz
info: sysdep_dsp: using alsa plugin
error: unable to find simple control. Socket operation on non-socket.

```

...I have set everything else to use Pulse. 

Is there a way I can force xmame to use pulse as well?

EDIT: this is a bit odd. I just ran another rom whilst playing music and xmame started to play a sound from the game (it's a very distinctive game and sound), then stopped. I'm not sure what this means, but I thought it might mean something to somebody! ;-)

---

### Post by dchurch24 on 2009-11-11
Oops - I must have had a brain relapse or something.

I did: man xmame

and found the -dp switch.

xmame -dp esound

solved the problem.

---

