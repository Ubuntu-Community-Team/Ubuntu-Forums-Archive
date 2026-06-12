---
title: "mplayer + quicktime"
date: 2006-01-12
forum: General Help
---

### Post by Chris Tucker on 2006-01-12
I use mplayer a lot (i mean a LOT. i use it primarily in geexbox right now while im getting my ubuntu installation to behave the same way for video files) and i have noticed that the included codec for quicktime doesnt properly cover all quicktime formats.

has anyone else had a problem where certain quicktime files wont play their sound in mplayer? has anyone found a codec addin to fix this? i have a LOT of quicktime files, of which about 1/3 are like this.

---

### Post by Thirsteh on 2006-01-12
[www.mplayerhq.hu](www.mplayerhq.hu) -- try downloading the essential codecs package, unpack, move to /usr/lib/win32  (have to create the folder) ... issue this command:

sudo ln -s /usr/lib/win32 /usr/lib/codecs

then try playing the movie again.

---

