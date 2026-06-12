---
title: "AVI files unplayable using totem"
date: 2009-04-22
forum: General Help
---

### Post by Julius1988 on 2009-04-22
I am getting the following error when i try to play avi files using TOTEM.Where to find the decoder?How to install them?
```

The playback of this movie requires the following decoders which are not installed:

MPEG-1 Layer 3 (MP3) decoder
DivX MPEG-4 Version 5 decoder

```

---

### Post by zero777zero on 2009-04-22
go to Add/Remove->Show: change to show All Applications, type in "restricted extras"

i also recommend you download VLC movie player from Add/Remove

---

### Post by Julius1988 on 2009-04-22
I have VLC and restricted extras but still not working.

---

### Post by Shunsuke_01 on 2009-04-22
Do other codecs work fine? Like MP3, MP4 etc.

Maybe you should try MPLayer. I prefer that over VLC.

---

### Post by FredB on 2009-04-22
Strange that you cannot play these files. Try adding medibuntu repository.

See [http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by Julius1988 on 2009-04-22
Yeah i added medibuntu repos and installed w32codecs..........but still i am not able to play
Here is the last part of my sources.list
```

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://packages.medibuntu.org/ intrepid free non-free

```
I wish to get the job done in totem.Even in VLC the video freezes and does not play smoothly.The same video plays fine in windows so there is no problem in the video.

---

