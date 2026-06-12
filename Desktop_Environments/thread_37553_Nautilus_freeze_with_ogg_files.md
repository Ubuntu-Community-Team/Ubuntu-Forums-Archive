---
title: "Nautilus freeze with ogg files"
date: 2005-05-27
forum: Desktop Environments
---

### Post by Jergar on 2005-05-27
Hi,
Nautilus freeze when i try to check the properties (with rigth mouse click)  of an ogg-vorbis file. This did not happen with an mp3-file. What could be wrong?

Regards
Jergar
Ubuntu 5.04

---

### Post by cutOff on 2005-05-27
[QUOTE=Jergar]Hi,
Nautilus freeze when i try to check the properties (with rigth mouse click)  of an ogg-vorbis file. This did not happen with an mp3-file. What could be wrong?

Regards
Jergar
Ubuntu 5.04[/QUOTE]
I'm not sure, try to install 'gstreamer0.8-ffmpeg' package

$ sudo aptitude install gstreamer0.8-ffmpeg

---

### Post by Jergar on 2005-05-27
To sad this does not help. Thanks!

Jergar

---

### Post by Burgundavia on 2005-05-27
This is known bug in Nautilus, fixed for gstreamer in Nautilus 2.11 and still broken for xine. 

Corey

---

### Post by Jergar on 2005-05-28
[QUOTE=Burgundavia]This is known bug in Nautilus, fixed for gstreamer in Nautilus 2.11 and still broken for xine. 

Corey[/QUOTE]

Many thanks, so I have to wait.

Jergar

---

