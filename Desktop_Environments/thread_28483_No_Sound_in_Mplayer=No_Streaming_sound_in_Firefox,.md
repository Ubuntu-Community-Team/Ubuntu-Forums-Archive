---
title: "No Sound in Mplayer=No Streaming sound in Firefox, help!"
date: 2005-04-20
forum: Desktop Environments
---

### Post by derrick1985 on 2005-04-20
Hi, i've been following the guide at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) as to getting streaming content up and running with Firefox, but the problem is I get Video, but no sound. I thought it might be with the streams but when I try to open up a video (which works in xine) i get the same thing, no sound. 

I tried to adjust the sound settings in preferences (alsa to oss, etc) but that doesn't work either. it also doesn't appear to save the changes I make when I do make them. When I chose OSS instead of Alsa, and restarted Mplayer, it was back on Alsa!

Help!

Thanks.

---

### Post by bored2k on 2005-04-20
[QUOTE=derrick1985]Hi, i've been following the guide at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) as to getting streaming content up and running with Firefox, but the problem is I get Video, but no sound. I thought it might be with the streams but when I try to open up a video (which works in xine) i get the same thing, no sound. 

I tried to adjust the sound settings in preferences (alsa to oss, etc) but that doesn't work either. it also doesn't appear to save the changes I make when I do make them. When I chose OSS instead of Alsa, and restarted Mplayer, it was back on Alsa!

Help!

Thanks.[/QUOTE]
 Hoary works by default with eSound [ESD]. Make sure MPlayer is using ESD. Also, try disabling sound server and retry MPlayer.

---

### Post by derrick1985 on 2005-04-21
[QUOTE=bored2k]Hoary works by default with eSound [ESD]. Make sure MPlayer is using ESD. Also, try disabling sound server and retry MPlayer.[/QUOTE]

Thanks, one part is solved. Sound now works in Mplayer, but still I get no sound through streaming! the file is a .mov file, if that means anything.

---

### Post by Sonic-NKT on 2005-04-21
its the same problem i thin.. firefox dont uses ESD too

try "pkill esd" and then try to stream it (restart firefox and everything)

---

### Post by rog62 on 2008-05-14
The easy way, just uninstall mplayer and everything works in Firefox!

---

