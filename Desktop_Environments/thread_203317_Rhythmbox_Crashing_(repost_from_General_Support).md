---
title: "Rhythmbox Crashing (repost from General Support)"
date: 2006-06-25
forum: Desktop Environments
---

### Post by Sale on 2006-06-25
So...Rhythmbox 0.9.3.1 on Ubuntu 6.06 crashes when I try to import my music folder into the library. The folder is on the NTFS partition, and Amarok, XMMS and other pplayers did not have any problems with that earlier (this is a new install of Ubuntu, on a new hard drive, and I'd preffer not to install multiple music players, I've had 6.06 before).

What Rhythmbox does is start building the library, imports some of the songs, and disapperas. So far it had imported 201 songs (out of more than 4000) and it doesn't seem to be going anywhere further.

BTW, I've installed everything mentioned on the:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by slider on 2006-06-25
Rhythmbox 0.9.3.1 crashes anytime gstreamer fails to parse a file. If you go to the Rhythmbox website there is a workaround involving checking the logs for the failed import, removing the file and starting the import again (and again) (and again). Rhythmbox 0.9.4.1 has a fix for this but you'll have to build it from source. When I did that it gave a nice readout of failed files rather than crashing. Turns out it was dying trying to read my .m3u playlists and .mp4 files.

---

### Post by Sale on 2006-06-25
[QUOTE=slider]Rhythmbox 0.9.3.1 crashes anytime gstreamer fails to parse a file. If you go to the Rhythmbox website there is a workaround involving checking the logs for the failed import, removing the file and starting the import again (and again) (and again). Rhythmbox 0.9.4.1 has a fix for this but you'll have to build it from source. When I did that it gave a nice readout of failed files rather than crashing. Turns out it was dying trying to read my .m3u playlists and .mp4 files.[/QUOTE]

Yes, that seems to be exactly what is happenning...oddly, earlier versions (in breezy and hoary didnt have this problem) :confused: 

Anyway, hanks for the explanation :)

---

