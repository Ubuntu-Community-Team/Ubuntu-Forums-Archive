---
title: "audacious not playing WMA files"
date: 2009-03-21
forum: General Help
---

### Post by richardy on 2009-03-21
Hi,
Having a few issues with audacious not playing WMA files. I have downloaded the relavant package to play WMA files within audacious but still wont play them correctly - plays other files formats (eg mp3) fine. I get an error saying "no output plugin selected - you have not selected an output plugin" when i attempt to close audacious. I also get the following error while a WMA song is trying to play: "overflow in spectral RLE, ignoring"

Any help with this would be much apreciated.

Cheers.

---

### Post by zvacet on 2009-03-21
Do you have w32 codecs installed?If you don´t add Medibuntu repo to your source list and after that install w32 codecs.[Here]("https://help.ubuntu.com/community/Medibuntu") is link about adding medibuntu to source list.

---

### Post by richardy on 2009-03-24
Hi,
Thanks for the reply. I installed all the codecs but still having no luck getting audacious to play WMA. I also have totem and the listen media players and they also will not play WMA. I checked the audacious plugins preferences and the WMA plugin (wma.so) is definitely there and enabled.

Any more ideas. Thanks for your help.

Cheers.

---

### Post by mc4man on 2009-03-24
It depends on what type of wma, if it's wma lossless than your best bet is amarok (with w32codecs and libxine1-ffmpeg) and mplayer (w32codecs

If they're wma pro (wma3) then it's hit or miss depending on the Khz and resolution though again amarok and mplayer are most likely.

---

