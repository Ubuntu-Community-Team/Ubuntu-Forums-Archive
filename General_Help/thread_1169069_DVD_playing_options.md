---
title: "DVD playing options"
date: 2009-05-24
forum: General Help
---

### Post by ncdryden on 2009-05-24
I have Ubuntu 8.10 on my Hp Pavillion ze4400 and cannot seem to get DVDs to play correctly, I have downloaded Totem-xine, gxine, Kaffine, Ogle, VLC and the default Mplayer no program seems to work. I did get Medibuntu and did everything I could to open the restricted formats, but DVD playback seems to be my only problem anybody got ideas that could help me???
PS I cannot get default Xine either.

---

### Post by SuperSonic4 on 2009-05-24
Did you download libdvdcss2? That package allows you to unscramble DVDs

```
sudo apt-get install libdvdcss2
```

---

### Post by ncdryden on 2009-05-24
Yes i have been wondering if it might have something to do with the buffer or bitrate because when the movie goes forward a bit then I rewind it the part that was loaded up to the stop point plays correctly.

---

