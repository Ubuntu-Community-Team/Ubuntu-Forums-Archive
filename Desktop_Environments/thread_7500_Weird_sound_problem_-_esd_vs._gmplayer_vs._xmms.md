---
title: "Weird sound problem - esd vs. gmplayer vs. xmms"
date: 2004-12-08
forum: Desktop Environments
---

### Post by kmoz on 2004-12-08
I've spent the better part of tonight on this and various other forums and google, and I still haven't quite got my sound working like I want it to.  Here goes:

Normally, I log in and system sounds work fine.  I can listen to mp3s in xmms with no problems.  When I try and watch a video with gmplayer though, I'm told that /dev/dsp audio can not be found.

Killing esd and/or restarting it with "esd -as 2" seems to allow gmplayer to access /dev/dsp.  I'm suspecting that the /etc/esound/esd.conf settings are not run properly by the system during boot/login.  Can anyone help me figure out if this is the case?  I'd rather not have to permanently disable esd (which is the solution to get audio in gmplayer), since audio works fine in xmms....any ideas?

---

### Post by poofyhairguy on 2004-12-08
[QUOTE=kmoz]I've spent the better part of tonight on this and various other forums and google, and I still haven't quite got my sound working like I want it to.  Here goes:

Normally, I log in and system sounds work fine.  I can listen to mp3s in xmms with no problems.  When I try and watch a video with gmplayer though, I'm told that /dev/dsp audio can not be found.

Killing esd and/or restarting it with "esd -as 2" seems to allow gmplayer to access /dev/dsp.  I'm suspecting that the /etc/esound/esd.conf settings are not run properly by the system during boot/login.  Can anyone help me figure out if this is the case?  I'd rather not have to permanently disable esd (which is the solution to get audio in gmplayer), since audio works fine in xmms....any ideas?[/QUOTE]


Use Xine? Seriously, I had the same problem, so I decied that Mplayer simply wasn't worth it.

---

