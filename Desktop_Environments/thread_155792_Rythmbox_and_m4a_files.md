---
title: "Rythmbox and m4a files"
date: 2006-04-05
forum: Desktop Environments
---

### Post by JDavid5381 on 2006-04-05
Does anyone know of a pluggin thats easy to install for Rythmbox so that it can play m4a audio files?  Right now I just use Beep Media Player with a pluggin, but Beep isn't really user friendly. If there isn't, does anyone know of a another music player with all the capabilities of rythmbox with a friendly GUI and plays m4a files thats easily installable for Ubuntu? 

Thanks,
James

---

### Post by feydrutha on 2006-04-13
Bump!

m4a is just the aac wrapper format, to which iTunes rips CDs by default (yes I was fooled into ripping some CDs to this friggin' format too).

I have installed gstreamer0.8-faad, and it is working since I can listen to my m4a in totem (with totem-gstreamer installed, not totem-xine).

But rhythmbox still says it does not have a codec. Anyone have a clue what the problem could be?

Paolo

---

### Post by hotani on 2006-04-13
I'm listening to AAC files in rhythmbox (sans iStore files.... fawkin' DRM), you have to enable a bunch of the gstreamer packages for it to work. It took me a few tries to get all the necessary ones - I think there were a few "bad" and "ugly" ones in there too.

---

### Post by feydrutha on 2006-04-14
I am using ubuntu 5.10, which uses gstreamer0.8, which doesn't have the good/bad/ugly division.

Anyway I have gstreamer decoder for aac (gstreamer-faad) and it's working, or I wouldn't be able to play those same m4a files in totem (with totem-gstreamer).

---

