---
title: "Music Codecs"
date: 2008-12-19
forum: General Help
---

### Post by JonBrown on 2008-12-19
Most of my music won't play on any of the music players because of the No Codecs error.  I have tried searching and installing different packages from searching Google and here.  To no avail they all say either that my packages are already up to date or that the package does not exist.  I am sure that this is something really simple but your help would be greatly appreciated.

---

### Post by SuperSonic4 on 2008-12-19
Do you have medibuntu sources installed?

---

### Post by JonBrown on 2008-12-19
I may have those installed I have tried installing everything I can find can you give me the sudo for them please?

---

### Post by taurus on 2008-12-19
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by JonBrown on 2008-12-21
Sorry for the late reply but it still didn't work.

---

### Post by abhilashm86 on 2008-12-21
go to synaptic package manager,there a list of codecs,just install....

anyways may i know what music codec u want,is it mp3's and videos codecs?

---

### Post by abhilashm86 on 2008-12-21
try this from terminal,audio codecs are generally done implicitly by ubuntu,just run

 sudo apt-get install rhythmbox

---

### Post by mc4man on 2008-12-21
You should probably just mention a couple of players and what format(s) your music files are.

In addition to the mentioned ubuntu-restricted-extras these will prove useful for xine based players and mplayer. (assumes you added medibuntu to sources

```
sudo apt-get install flac faad libxine1-ffmpeg w32codecs
```

---

