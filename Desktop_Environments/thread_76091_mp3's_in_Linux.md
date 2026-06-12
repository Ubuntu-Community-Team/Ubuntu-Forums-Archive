---
title: "mp3's in Linux"
date: 2005-10-14
forum: Desktop Environments
---

### Post by seismicmike on 2005-10-14
Hey, I'm looking for an mp3 player that works in Linux. Do you know of one, and how I can install it?

---

### Post by aysiu on 2005-10-14
My Sandisk 256 MB MP3 player works well with every distro I've tried (including Ubuntu). You don't have to install anything. It's just drag-n-drop.

---

### Post by TristanMike on 2005-10-14
Under Applications-->Sound & Video-->Music Player (aka Rhythmbox) can play mp3's but you need to install a few things to get mp3 to work. But the wiki can tell you better than I can, so, [here it is](https://wiki.ubuntu.com/RestrictedFormats). You can find it under Codecs and DVD-Video.

But if that don't float your boat, then I've heard Beep-Media-Player and XMMS are fine players.

---

### Post by seismicmike on 2005-10-14
i'm having problems with the instructions there... the apt-gets i try to do are not working.... "such and such file was not found but was referred to by another package"

Beep freezes on me..

i also have real player 10 apparently, but it doesn't work.... :(

---

### Post by leaber on 2005-10-15
have you tried XMMS?? its like winamp...
i'm not an expert and i havent tried all the options, but this worked from the first time

Here is the how-to of the installation:
[http://www.ubuntuguide.org/#xmms]("http://www.ubuntuguide.org/#xmms")

hope it helps

---

### Post by doclivingston on 2005-10-15
[QUOTE=seismicmike]i'm having problems with the instructions there... the apt-gets i try to do are not working.... "such and such file was not found but was referred to by another package"([/QUOTE]

Did you enable the "universe" repository? If so, installing the "gstreamer0.8-mad" (for mp3 support) or "gstreamer0.8-plugins" (mp3 and more codecs) package should work.

---

