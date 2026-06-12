---
title: "Proper media playback support."
date: 2005-10-21
forum: Desktop Environments
---

### Post by Armagguedes on 2005-10-21
[SIZE=2]Hello.

I watch a lot of anime, not to mention audiofiles, but i'm stuck because kubuntu.breezy needs all the codecs to be hand-installed. These are what i need:
[/SIZE] [INDENT][SIZE=2][SIZE=1]ac3
ape
avi
divx (divx4,5,6)
flac
h.264 x.264
matroska (mka, mkv)
mp3
mp4
vorbis (ogg ogm)
wma, wmv
xvid
subtitle rendering/wtv[/SIZE]
ETC...
  [/SIZE][/INDENT] [SIZE=2]
Also i would like to know which players are more adequate for video files and audio files. Currently i have [SIZE=1]amaroK[/SIZE] and [SIZE=1]Kaffeine[/SIZE] installed, but input is appreciated (i still haven't used them).

Thanks for your help.
Cheers
[/SIZE]

---

### Post by Predius on 2005-10-21
Try to use the w32 codecs.

[http://debian.tu-bs.de/mplayer/ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/w32codecs_20050412-0.0_i386.deb]("http://debian.tu-bs.de/mplayer/ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/w32codecs_20050412-0.0_i386.deb")

---

### Post by Armagguedes on 2005-10-21
[quote=Predius]Try to use the w32 codecs.

[http://debian.tu-bs.de/mplayer/ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/w32codecs_20050412-0.0_i386.deb]("http://debian.tu-bs.de/mplayer/ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/w32codecs_20050412-0.0_i386.deb")[/quote] 
Ok tks. I already knew about this from mplayer's site, but which formats does this support? 

Instead i went to mplayer's site and just installed the all-codec pack (into /opt/codecs). Anyone know which formats are **not** supported in this pack?

---

### Post by bored2k on 2005-10-22
[http://kambing.vlsm.org/ubuntu-backports/hoary-extras/restricted/binary-i386/x264-bin_0.cvs20050419-0.0~5.04ubp1_i386.deb](http://kambing.vlsm.org/ubuntu-backports/hoary-extras/restricted/binary-i386/x264-bin_0.cvs20050419-0.0~5.04ubp1_i386.deb)
[http://kambing.vlsm.org/ubuntu-backports/hoary-extras/restricted/binary-i386/libx264-dev_0.cvs20050419-0.0~5.04ubp1_i386.deb](http://kambing.vlsm.org/ubuntu-backports/hoary-extras/restricted/binary-i386/libx264-dev_0.cvs20050419-0.0~5.04ubp1_i386.deb)

Pretty much everything is in w32codecs.

---

