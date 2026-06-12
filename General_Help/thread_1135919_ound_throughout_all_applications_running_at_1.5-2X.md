---
title: "ound throughout all applications running at 1.5-2X speed above normal"
date: 2009-04-24
forum: General Help
---

### Post by maravingian on 2009-04-24
Upgraded yesterday from Ubuntu 8.10 32 bit to 9.04 64 bit and one problem arose.  System wide increase in bitrate for sound.  Opening sound for login screen runs too fast.  Video on internet (youtube etc) runs erratically - slows at times and then speeds up to over catch up. Playing a CD or listening to music from playlists using totem, rhythmbox etc causes sound to run too fast, 1.5 x faster.  videos played using gstreamer, vlc, movie player causes the video to pixelate then speed up VT.  Audio tends to run in the same way as the video problems.  iPlayer runs then reloads every 3 seconds.

Does anyone have any ideas???????

AMD Athlon 64 2X Dual Core 6000+, 89.9 GB HDD, 875.8MB RAM, GeForce 7050 PV / NVIDIA nForce 630a, Ubuntu 9.04 amd64

---

### Post by paradigm2 on 2009-04-24
> **maravingian said:**
> Upgraded yesterday from Ubuntu 8.10 32 bit to 9.04 64 bit and one problem arose.  System wide increase in bitrate for sound.  Opening sound for login screen runs too fast.  Video on internet (youtube etc) runs erratically - slows at times and then speeds up to over catch up. Playing a CD or listening to music from playlists using totem, rhythmbox etc causes sound to run too fast, 1.5 x faster.  videos played using gstreamer, vlc, movie player causes the video to pixelate then speed up VT.  Audio tends to run in the same way as the video problems.  iPlayer runs then reloads every 3 seconds.

Does anyone have any ideas???????

AMD Athlon 64 2X Dual Core 6000+, 89.9 GB HDD, 875.8MB RAM, GeForce 7050 PV / NVIDIA nForce 630a, Ubuntu 9.04 amd64


Which sound card have you?

```

lspci

```

in terminal.

---

### Post by maravingian on 2009-04-25
My soundcard is a: nVidia Corporation MCP67 High Definition Audio (rev a1)

---

### Post by Labello on 2009-05-06
I have got the same problem with the following soundcard:

Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive

but my other one:

Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller

in the same PC with the same kernel works just fine. but i prefer the other one because i can turn it up much louder.

---

