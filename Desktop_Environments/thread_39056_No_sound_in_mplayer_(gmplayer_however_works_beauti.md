---
title: "No sound in mplayer (gmplayer however works beautifully)"
date: 2005-06-03
forum: Desktop Environments
---

### Post by techmonkey on 2005-06-03
This is peculiar. I installed mplayer after I followed the howto on UF here on how to get multiple sounds playing at once, with alsa/esd software mixing, and everything is great; If I was so inclined, I could watch two videos at a time -- in VLC and Mplayer.

I'm not going to, practically, but it's nice to know that I can and that it works.

Anyway, gmplayer was starting to become one of my favourite media players again when I decided to play something in console:

mplayer <path to>.mp3
mplayer -ao esd ...
mplayer -ao sdl ...
mplayer -ao alsa...

All result in the 'Could not open/initialize audio device -> No sound' error message. A temporary workaround is to use -ao oss and wrap it in esddsp so that mplayer uses the OSS driver, but sends it through ESD; This however means that even though it goes through ESD, it's still OSS sound, and thus mplayer is the only thing that can be playing sound at that moment -- which is a bit pointless after following the (brilliant) howto on ALSA software mixing.

This happens both when nothing else is playing, and when other sounds are playing. Gmplayer happily uses the ALSA driver so that ALSA can throw mplayer's audio output into the sound mix. But not console-mode mplayer, which I can't understand.

Does gmplayer just not use /etc/mplayer/mplayer.conf, and there's something in there I need to tweak? Because it just seems so odd to me that the core of mplayer works in graphical mode (the gmplayer client) and then *not*, in the console mode (mplayer itself).

I may also seek out a vlc-remote; I'm guessing one must exist -- it's the only thing mplayer has that VLC doesn't seem to. Maybe Mplayer has had its day.  :-|

---

