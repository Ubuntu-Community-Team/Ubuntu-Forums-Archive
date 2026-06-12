---
title: "noatun doesn't work"
date: 2005-10-15
forum: Desktop Environments
---

### Post by ryke on 2005-10-15
Hi,

I've made a fresh installation of K 5.10 (btw, with a lot of problems :-( ... no problems with my old 5.04)

XMMS, Kaffeine and Xine works ok, but Noatun doesn't. The program starts and for a couple minutes show the title of the file to be played (blinking), with none sound, and afterthat it closes without giving any error message.

I've reinstalled it 2 times, but problem hasn't been solved. It doesn't play anything (mp3 nor avis).

any idea?

thnx in advance ;-)

---

### Post by tag on 2005-10-15
Similar problem here. I upgraded from hoary and since then noatun starts but cannot play a single file (be it video or audio) it just skips through the playlist without playing anything. Eventually it crashes...  any ideas? xine and kaffeine work fine though.

---

### Post by agm642 on 2005-10-15
Try running noatun through the command line and posting the output here.

---

### Post by ryke on 2005-10-15
hi... running from the Console, no message is displayed... after a couple of minutes noatun finishes and nothing more happens.

regards

---

### Post by tag on 2005-10-15
same here. I run it from the console and as I quit (via tray->quit) i get the message "noatun: ERROR: Communication problem with noatun, it probably crashed." Guess that doesn't help much.

---

### Post by Segovia on 2005-10-15
I don't think it's Kubuntu specific, since Noatun in my Fedora Core 4 install does exactly the same thing as it does in Kubuntu...  doesn't play anything and eventually crashes as it tries to cycle through every mp3 in the playlist.

---

### Post by sinbad782 on 2005-10-15
Might this be a problem of not having the codecs installed for dealing with restricted formats?

If it is, then this page may give a few tips:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Takis on 2005-10-15
I think there may be a problem with arts, the KDE sound daemon. I've noticed that if I try and use the arts plugin for XMMS, it won't play, but if I tell it to use ALSA, it works. I think Noatun only uses arts, which may explain why it never works.

Edit: It doesn't look like arts. XMMS plays WMAs fine, but stuffs up MP3s and OGGs. What the...?

---

### Post by ryke on 2005-10-16
hi,

well, noatun worked perfectly some days ago with Hoary, and it was capable to play mp3, avi, rm and everything ;-)

regarding codecs, the only difference (I think) is that now I don't have installed the w32codecs (I've installed them from a debian package, but xmms doesn't work, so I uninstalled them)

---

### Post by tag on 2005-10-16
I have all codecs installed and the other players seem to acknowledge that. I don't know what else could be wrong

---

### Post by Takis on 2005-10-16
ROFL sorry on a side note the fat kid in your avatar is dancing exactly in tune to what I'm listening to, tag. :D

If only that would fix this stupid problem.

---

### Post by tag on 2005-10-16
Me? Fat? No way! ;-) I'm an avid McDonalds dietist :-)

---

### Post by tag on 2005-10-16
Wow...now i got some output on the console:
> 
(The previous message was repeated 1 times.)
mimetype video/quicktime unsupported
mimetype video/quicktime unsupported
(The previous message was repeated 8 times.)
mimetype video/x-msvideo unsupported
mimetype video/x-msvideo unsupported
(The previous message was repeated 4 times.)
mimetype video/mp4 unsupported
mimetype video/x-msvideo unsupported
mimetype video/mp4 unsupported
mimetype video/x-msvideo unsupported

note that i have w32codecs installed

---

### Post by Segovia on 2005-10-16
[QUOTE=sinbad782]Might this be a problem of not having the codecs installed for dealing with restricted formats?[/QUOTE]

I don't think so.  I've got all the GStreamer plugins and Xine/MPlayer codecs.  But oddly, today Noatun can play mp3's in Kubuntu.  No idea why.  There were no updates.

Still not working in Fedora (every other software *but* Noatun can play them)... which doesn't really matter at this point, since FC4 is about to get obliterated from that HDD today.  The KDE implementation is pretty poor, compared to Kubuntu.

---

### Post by tlindner on 2005-10-17
Same problem here... plays vorbis files fine...   but when it plays mp3s, it just loops and loops until i do a "killall noatun"

---

### Post by yoshic on 2006-01-08
Well, same problem here, andi can't get noatun working :confused: ](*,), 

but in my case, i was using gnome first, and then i worked, but when i changed to kubuntu the problems begin....:mad:

---

